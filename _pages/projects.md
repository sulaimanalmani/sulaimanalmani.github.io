---
layout: page
title: projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: true
nav_order: 3
display_categories: [work]
horizontal: true
---

<div class="projects">
{% assign categories = page.display_categories | default: empty %}

{% if site.enable_project_categories and categories and categories != empty %}
{% for category in categories %}
<a id="{{ category | downcase }}" href="#{{ category | downcase }}"><h2 class="category">{{ category }}</h2></a>
{% assign categorized_projects = site.projects | where: "category", category %}
{% assign sorted_projects = categorized_projects | sort: "importance" %}
<div class="row">
{% if sorted_projects and sorted_projects != empty %}
{% for project in sorted_projects %}
{% include project_horizontal_full.liquid project=project %}
{% endfor %}
{% else %}
<div class="col-12 mb-4"><p class="text-muted">No projects in “{{ category }}”.</p></div>
{% endif %}
</div>
{% endfor %}
{% else %}
{% assign sorted_projects = site.projects | sort: "importance" %}

  <div class="row">
    {% if sorted_projects and sorted_projects != empty %}
      {% for project in sorted_projects %}
        {% include project_horizontal_full.liquid project=project %}
      {% endfor %}
    {% else %}
      <div class="col-12"><p class="text-muted">No projects found.</p></div>
    {% endif %}
  </div>
{% endif %}
</div>
