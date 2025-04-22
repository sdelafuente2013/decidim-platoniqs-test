# Decidim Test - Configuración e Instalación

Este repositorio contiene mi solución para el test técnico de Platoniqs relacionado con Decidim, una plataforma de participación ciudadana desarrollada en Ruby on Rails.

## Sobre Decidim

Decidim es un proyecto tecnopolítico. Una plataforma digital de participación ciudadana para una ciudad democrática, desarrollada de forma abierta y colaborativa utilizando software libre. Es una infraestructura pública de bienes comunes. Pública porque cuenta con un claro impulso institucional y de bienes comunes porque el código es abierto y libre, es decir, cualquiera puede verlo, usarlo, copiarlo o modificarlo.

## Pasos realizados

### 1. Instalación de Decidim

- Cloné el repositorio oficial de Decidim desde GitHub
- Seguí el tutorial de instalación para configurar el entorno de desarrollo mediante Docker
- Verifiqué que la aplicación base funcionara correctamente

### 2. Instalación de módulos adicionales

Añadí los siguientes módulos según lo solicitado:

#### Decidim::AlternativeLanding

Este módulo permite personalizar la página de inicio de Decidim con un diseño alternativo.

Añadí la gema al Gemfile:

```ruby
gem "decidim-alternative_landing", git: "https://github.com/Platoniq/decidim-module-alternative_landing"
```

#### Decidim::DecidimAwesome

Este módulo añade funcionalidades y personalizaciones adicionales a Decidim.

Añadí la gema al Gemfile:

```ruby
gem "decidim-decidim_awesome", github: "decidim-ice/decidim-module-decidim_awesome", branch: "main"
```

### 3. Solución a problemas de compatibilidad

Durante la instalación, encontré un problema de compatibilidad con la versión 0.29.1 de Decidim. Para resolverlo, creé el siguiente archivo:

`app_code/config/initializers/decidim_attributes_richtext_fix.rb`

```ruby
module Decidim
  module Attributes
    class RichText < String
      def self.type
        String
      end
    end unless defined?(RichText)
  end
end
```

Este arreglo permite que los módulos instalados funcionen correctamente con la versión actual de Decidim.

### 4. Publicación del trabajo

- Creé un repositorio en GitHub para hospedar el proyecto
- Realicé un commit inicial con la instalación base de Decidim
- Creé un Pull Request, para mantener un registro claro de los cambios realizados
- Finalicé la integración y documenté el proceso

## Problemas encontrados y soluciones

Durante el desarrollo del test, encontré algunos desafíos:

1. **Incompatibilidad de versiones**: El módulo DecidimAwesome inicialmente presentó problemas de compatibilidad con la versión de Decidim que estaba utilizando. La solución fue crear el archivo fix mencionado anteriormente.

2. **Dependencias**: Algunos módulos requerían dependencias adicionales que no estaban claramente documentadas. Fue necesario investigar y resolver estas dependencias manualmente.

## Conclusiones

La plataforma Decidim ofrece una base sólida para la participación ciudadana digital, y los módulos adicionales permiten extender su funcionalidad de manera significativa. El proceso de instalación y configuración requiere cierta familiaridad con Ruby on Rails, pero la documentación oficial proporciona una guía útil para comenzar.

El módulo AlternativeLanding ofrece opciones interesantes para personalizar la experiencia del usuario en la página de inicio, mientras que DecidimAwesome añade herramientas de personalización avanzadas que pueden ser muy útiles para implementaciones específicas.

## Recursos adicionales

- [Documentación oficial de Decidim](https://docs.decidim.org/)
- [Repositorio de Decidim en GitHub](https://github.com/decidim/decidim)
- [Módulos disponibles para Decidim](https://decidim.org/modules)
