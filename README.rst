Blend-ed-theme can be installed as a Tutor plugin::

    tutor local stop
    cd $(tutor config printroot)/env/build/openedx/requirements
    git clone https://github.com/blend-ed/tutor-blend-ed-theme
    pip install -e ./tutor-blend-ed-theme
    tutor plugins enable blend-ed-theme
    tutor config save

Rebuild the Openedx docker image::

    tutor images build openedx

Restart your platform::

    tutor local start -d

You will then have to enable the "blend-ed-theme" theme, as per the `Tutor documentation <https://docs.tutor.overhang.io/local.html#setting-a-new-theme>`__::

    tutor local do settheme blend-ed-theme

Configuration
-------------

- ``BLEND_ED_WELCOME_MESSAGE`` (default: "Learning in all dimensions")
- ``BLEND_ED_PRIMARY_COLOR`` (default: "#009cc7")
- ``BLEND_ED_FOOTER_NAV_LINKS`` (default: ``[{"title": "About", "url": "/about"}, {"title": "Contact", "url": "/contact"}]``)
- ``BLEND_ED_FOOTER_LEGAL_LINKS`` (default: ``[{"title": "Terms of service", "url": "/tos"}, {"title": "BLEND_ED theme for Open edX", "url": "https://github.com/overhangio/tutor-BLEND_ED"}]``)

The ``BLEND_ED_*`` settings listed above may be modified by running ``tutor config save --set BLEND_ED_...=...``. For instance, to remove all links from the footer, run::

    tutor config save --set "BLEND_ED_FOOTER_NAV_LINKS=[]" --set "BLEND_ED_FOOTER_LEGAL_LINKS=[]"