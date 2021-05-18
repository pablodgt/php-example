If your project depends on the Advanced Custom Fields plugin, Dependabot won't be able to download it via the usual mechanisms that rely on the presence of an `ACF_PRO_KEY` environment variable (e.g., https://github.com/pivvenit/acf-composer-bridge).

Instead, if you're working in a **private** repository, we recommend vendoring your **licensed** copy of the Advanced Custom Fields plugin in your repository. This branch illustrates this approach.

### Caveats

First some caveats:

- By using this approach, Dependabot will be able to update the rest of your composer project's dependencies. However, to update your Advanced Custom Fields plugin, you'll need to manually [download a zip file](https://wordpress.org/plugins/advanced-custom-fields/) with the desired version and commit the contents to your repository.
- This is not legal advice. If you're concerned about the legality of committing the contents of the Advanced Custom Fields plugin in your private repository, please consult your legal counsel.

### Set up

1. Download a licensed copy of the advanced-custom-fields plugin at https://wordpress.org/plugins/advanced-custom-fields.
2. At the root of your project, unzip the contents into the `vendor` directory. (See [expected structure](#expected-directory-structure) below.)
3. Create a `composer.json` file at `vendor/advanced-custom-fields/composer.json` with the content seen in [`vendor/advanced-custom-fields/composer.json`](https://github.com/dependabot/php-example/blob/acf-pro-example/vendor/advanced-custom-fields/composer.json).
4. In your top-level `composer.json` file, add the following `repositories` entry as seen [here](https://github.com/dependabot/php-example/blob/acf-pro-example/composer.json#L7-L11):

    ```json
      "repositories": [
        {
          "type": "path",
          "url": "vendor/advanced-custom-fields"
        }
      ],
      ```
5. Run `composer update`.
6. Commit the changes to your repository.
7. Push your changes to GitHub.
8. The next time Dependabot Version Updates runs, it should successfully check for updates of your other composer dependencies.

#### Expected Directory Structure

If you're using advanced-custom-fields v5.9.5, your directory structure would have the following content:

```
├── composer.json
├── composer.lock
├── vendor
│   └── advanced-custom-fields
│       ├── README.md
│       ├── acf.php
│       ├── assets
│       │   ├── css
│       │   │   ├── acf-dark.css
│       │   │   ├── acf-field-group.css
│       │   │   ├── acf-global.css
│       │   │   └── acf-input.css
│       │   ├── images
│       │   │   ├── acf-logo.png
│       │   │   ├── spinner.gif
│       │   │   └── spinner@2x.gif
│       │   ├── inc
│       │   │   ├── datepicker
│       │   │   │   ├── images
│       │   │   │   │   ├── ui-bg_highlight-soft_0_ffffff_1x100.png
│       │   │   │   │   ├── ui-icons_444444_256x240.png
│       │   │   │   │   ├── ui-icons_DDDDDD_256x240.png
│       │   │   │   │   └── ui-icons_ffffff_256x240.png
│       │   │   │   ├── jquery-ui.css
│       │   │   │   └── jquery-ui.min.css
│       │   │   ├── select2
│       │   │   │   ├── 3
│       │   │   │   │   ├── select2-spinner.gif
│       │   │   │   │   ├── select2.css
│       │   │   │   │   ├── select2.js
│       │   │   │   │   ├── select2.min.js
│       │   │   │   │   ├── select2.png
│       │   │   │   │   └── select2x2.png
│       │   │   │   └── 4
│       │   │   │       ├── select2.css
│       │   │   │       ├── select2.full.js
│       │   │   │       ├── select2.full.min.js
│       │   │   │       ├── select2.js
│       │   │   │       ├── select2.min.css
│       │   │   │       └── select2.min.js
│       │   │   └── timepicker
│       │   │       ├── jquery-ui-timepicker-addon.css
│       │   │       ├── jquery-ui-timepicker-addon.js
│       │   │       ├── jquery-ui-timepicker-addon.min.css
│       │   │       └── jquery-ui-timepicker-addon.min.js
│       │   └── js
│       │       ├── acf-field-group.js
│       │       ├── acf-field-group.min.js
│       │       ├── acf-input.js
│       │       ├── acf-input.min.js
│       │       ├── acf.js
│       │       └── acf.min.js
│       ├── includes
│       │   ├── acf-field-functions.php
│       │   ├── acf-field-group-functions.php
│       │   ├── acf-form-functions.php
│       │   ├── acf-helper-functions.php
│       │   ├── acf-hook-functions.php
│       │   ├── acf-input-functions.php
│       │   ├── acf-meta-functions.php
│       │   ├── acf-post-functions.php
│       │   ├── acf-user-functions.php
│       │   ├── acf-utility-functions.php
│       │   ├── acf-value-functions.php
│       │   ├── acf-wp-functions.php
│       │   ├── admin
│       │   │   ├── admin-field-group.php
│       │   │   ├── admin-field-groups.php
│       │   │   ├── admin-notices.php
│       │   │   ├── admin-tools.php
│       │   │   ├── admin-upgrade.php
│       │   │   ├── admin.php
│       │   │   ├── tools
│       │   │   │   ├── class-acf-admin-tool-export.php
│       │   │   │   ├── class-acf-admin-tool-import.php
│       │   │   │   └── class-acf-admin-tool.php
│       │   │   └── views
│       │   │       ├── field-group-field-conditional-logic.php
│       │   │       ├── field-group-field.php
│       │   │       ├── field-group-fields.php
│       │   │       ├── field-group-locations.php
│       │   │       ├── field-group-options.php
│       │   │       ├── html-admin-navigation.php
│       │   │       ├── html-admin-page-upgrade-network.php
│       │   │       ├── html-admin-page-upgrade.php
│       │   │       ├── html-admin-tools.php
│       │   │       ├── html-location-group.php
│       │   │       ├── html-location-rule.php
│       │   │       └── html-notice-upgrade.php
│       │   ├── ajax
│       │   │   ├── class-acf-ajax-check-screen.php
│       │   │   ├── class-acf-ajax-local-json-diff.php
│       │   │   ├── class-acf-ajax-query-users.php
│       │   │   ├── class-acf-ajax-query.php
│       │   │   ├── class-acf-ajax-upgrade.php
│       │   │   ├── class-acf-ajax-user-setting.php
│       │   │   └── class-acf-ajax.php
│       │   ├── api
│       │   │   ├── api-helpers.php
│       │   │   ├── api-template.php
│       │   │   └── api-term.php
│       │   ├── assets.php
│       │   ├── class-acf-data.php
│       │   ├── compatibility.php
│       │   ├── deprecated.php
│       │   ├── fields
│       │   │   ├── class-acf-field-accordion.php
│       │   │   ├── class-acf-field-button-group.php
│       │   │   ├── class-acf-field-checkbox.php
│       │   │   ├── class-acf-field-color_picker.php
│       │   │   ├── class-acf-field-date_picker.php
│       │   │   ├── class-acf-field-date_time_picker.php
│       │   │   ├── class-acf-field-email.php
│       │   │   ├── class-acf-field-file.php
│       │   │   ├── class-acf-field-google-map.php
│       │   │   ├── class-acf-field-group.php
│       │   │   ├── class-acf-field-image.php
│       │   │   ├── class-acf-field-link.php
│       │   │   ├── class-acf-field-message.php
│       │   │   ├── class-acf-field-number.php
│       │   │   ├── class-acf-field-oembed.php
│       │   │   ├── class-acf-field-output.php
│       │   │   ├── class-acf-field-page_link.php
│       │   │   ├── class-acf-field-password.php
│       │   │   ├── class-acf-field-post_object.php
│       │   │   ├── class-acf-field-radio.php
│       │   │   ├── class-acf-field-range.php
│       │   │   ├── class-acf-field-relationship.php
│       │   │   ├── class-acf-field-select.php
│       │   │   ├── class-acf-field-separator.php
│       │   │   ├── class-acf-field-tab.php
│       │   │   ├── class-acf-field-taxonomy.php
│       │   │   ├── class-acf-field-text.php
│       │   │   ├── class-acf-field-textarea.php
│       │   │   ├── class-acf-field-time_picker.php
│       │   │   ├── class-acf-field-true_false.php
│       │   │   ├── class-acf-field-url.php
│       │   │   ├── class-acf-field-user.php
│       │   │   ├── class-acf-field-wysiwyg.php
│       │   │   └── class-acf-field.php
│       │   ├── fields.php
│       │   ├── forms
│       │   │   ├── form-attachment.php
│       │   │   ├── form-comment.php
│       │   │   ├── form-customizer.php
│       │   │   ├── form-front.php
│       │   │   ├── form-gutenberg.php
│       │   │   ├── form-nav-menu.php
│       │   │   ├── form-post.php
│       │   │   ├── form-taxonomy.php
│       │   │   ├── form-user.php
│       │   │   └── form-widget.php
│       │   ├── l10n.php
│       │   ├── legacy
│       │   │   └── legacy-locations.php
│       │   ├── local-fields.php
│       │   ├── local-json.php
│       │   ├── local-meta.php
│       │   ├── locations
│       │   │   ├── abstract-acf-legacy-location.php
│       │   │   ├── abstract-acf-location.php
│       │   │   ├── class-acf-location-attachment.php
│       │   │   ├── class-acf-location-comment.php
│       │   │   ├── class-acf-location-current-user-role.php
│       │   │   ├── class-acf-location-current-user.php
│       │   │   ├── class-acf-location-nav-menu-item.php
│       │   │   ├── class-acf-location-nav-menu.php
│       │   │   ├── class-acf-location-page-parent.php
│       │   │   ├── class-acf-location-page-template.php
│       │   │   ├── class-acf-location-page-type.php
│       │   │   ├── class-acf-location-page.php
│       │   │   ├── class-acf-location-post-category.php
│       │   │   ├── class-acf-location-post-format.php
│       │   │   ├── class-acf-location-post-status.php
│       │   │   ├── class-acf-location-post-taxonomy.php
│       │   │   ├── class-acf-location-post-template.php
│       │   │   ├── class-acf-location-post-type.php
│       │   │   ├── class-acf-location-post.php
│       │   │   ├── class-acf-location-taxonomy.php
│       │   │   ├── class-acf-location-user-form.php
│       │   │   ├── class-acf-location-user-role.php
│       │   │   └── class-acf-location-widget.php
│       │   ├── locations.php
│       │   ├── loop.php
│       │   ├── media.php
│       │   ├── revisions.php
│       │   ├── third-party.php
│       │   ├── updates.php
│       │   ├── upgrades.php
│       │   ├── validation.php
│       │   ├── walkers
│       │   │   ├── class-acf-walker-nav-menu-edit.php
│       │   │   └── class-acf-walker-taxonomy-field.php
│       │   └── wpml.php
│       ├── lang
│       │   ├── acf-ar.mo
│       │   ├── acf-ar.po
│       │   ├── acf-bg_BG.mo
│       │   ├── acf-bg_BG.po
│       │   ├── acf-ca.mo
│       │   ├── acf-ca.po
│       │   ├── acf-cs_CZ.mo
│       │   ├── acf-cs_CZ.po
│       │   ├── acf-de_CH.mo
│       │   ├── acf-de_CH.po
│       │   ├── acf-de_DE.mo
│       │   ├── acf-de_DE.po
│       │   ├── acf-de_DE_formal.mo
│       │   ├── acf-de_DE_formal.po
│       │   ├── acf-es_ES.mo
│       │   ├── acf-es_ES.po
│       │   ├── acf-fa_IR.mo
│       │   ├── acf-fa_IR.po
│       │   ├── acf-fi.mo
│       │   ├── acf-fi.po
│       │   ├── acf-fr_CA.mo
│       │   ├── acf-fr_CA.po
│       │   ├── acf-fr_FR.mo
│       │   ├── acf-fr_FR.po
│       │   ├── acf-he_IL.mo
│       │   ├── acf-he_IL.po
│       │   ├── acf-hr.mo
│       │   ├── acf-hr.po
│       │   ├── acf-hu_HU.mo
│       │   ├── acf-hu_HU.po
│       │   ├── acf-id_ID.mo
│       │   ├── acf-id_ID.po
│       │   ├── acf-it_IT.mo
│       │   ├── acf-it_IT.po
│       │   ├── acf-ja.mo
│       │   ├── acf-ja.po
│       │   ├── acf-nb_NO.mo
│       │   ├── acf-nb_NO.po
│       │   ├── acf-nl_NL.mo
│       │   ├── acf-nl_NL.po
│       │   ├── acf-pl_PL.mo
│       │   ├── acf-pl_PL.po
│       │   ├── acf-pt_BR.mo
│       │   ├── acf-pt_BR.po
│       │   ├── acf-pt_PT.mo
│       │   ├── acf-pt_PT.po
│       │   ├── acf-ro_RO.mo
│       │   ├── acf-ro_RO.po
│       │   ├── acf-ru_RU.mo
│       │   ├── acf-ru_RU.po
│       │   ├── acf-sk_SK.mo
│       │   ├── acf-sk_SK.po
│       │   ├── acf-sv_SE.mo
│       │   ├── acf-sv_SE.po
│       │   ├── acf-tr_TR.mo
│       │   ├── acf-tr_TR.po
│       │   ├── acf-uk.mo
│       │   ├── acf-uk.po
│       │   ├── acf-zh_CN.mo
│       │   ├── acf-zh_CN.po
│       │   ├── acf-zh_TW.mo
│       │   ├── acf-zh_TW.po
│       │   └── acf.pot
│       └── readme.txt
```
