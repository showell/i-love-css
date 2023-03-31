
# I F***ing LOVE CSS stylesheets! #"
# They are so damn elegant and composable!!! #
## How are you not understanding this??? ##

#### tooltips.css ####
~~~
[data-tippy-root] {
    /* Since tooltip elements are sometimes inside elements
     * which have different font-family, we force font-family
     * for tooltips here.
     */
    font-family: "Source Sans 3", sans-serif !important;
    word-wrap: break-word;
    /* Contains stylistic variant of upper-case character "I" in Source Sans 3 */
    font-feature-settings: "ss01" on;

    /* Affects all tippy tooltips not using any theme. */
    .tippy-box:not([data-theme]) {
        background: hsl(0deg 0% 20%);
        border-radius: 5px;
        min-height: 25px;
        box-sizing: border-box;

        .tippy-content {
            box-sizing: inherit;
            display: flex;
            align-items: center;
            padding: 5px 10px;
            font-size: 14px;
            line-height: 20px;
            color: hsl(0deg 0% 100%);
        }

        .tippy-arrow::before {
            /* This affects the arrow for tooltips and doesn't have any impact on arrows for popovers.
             * The transform property scales down the size of the arrow, giving it a thinner appearance.
             * https://atomiks.github.io/tippyjs/v6/themes/#changing-the-arrow-size
             */
            transform: scale(0.75);
        }

        .tooltip-inner-content {
            line-height: 17px;
        }

        &[data-placement^="top"] > .tippy-arrow::before {
            border-top-color: hsl(0deg 0% 20%);
        }

        &[data-placement^="bottom"] > .tippy-arrow::before {
            border-bottom-color: hsl(0deg 0% 20%);
        }

        &[data-placement^="left"] > .tippy-arrow::before {
            border-left-color: hsl(0deg 0% 20%);
        }

        &[data-placement^="right"] > .tippy-arrow::before {
            border-right-color: hsl(0deg 0% 20%);
        }
    }

    .tippy-arrow::before {
        /* `.tippy-arrow:before` element sometimes
         * inherits the height of the parent, we
         * don't want any height here since we
         * want it to remain an triangle.
         * The bug was only found in Firefox.
         */
        height: 0 !important;
    }
    /* If the text in the tooltips stretches to multiple lines,
     * we want the lines to be left-indented and not right-indented
     * by default.
     */
    text-align: left;

    .tooltip-hotkey-hints {
        box-sizing: inherit;
        display: flex;
        align-self: flex-start;
        margin: 0 -5px 0 10px;
        gap: 4px;
    }

    .tooltip-hotkey-hint {
        box-sizing: inherit;
        border: 1px solid hsl(225deg 100% 84%);
        border-radius: 3px;
        color: hsl(225deg 100% 84%);
        padding: 2px 5px;
        min-width: 20px;
        text-align: center;
        line-height: 14px;
    }
}

~~~
#### portico.css ####
~~~
body {
    background-color: hsl(0deg 0% 98%);
    font-family: "Source Sans 3", sans-serif;
    line-height: 150%;
    height: 100%;
    font-weight: 300;
    font-size: 17px;
}

html {
    height: 100%;
}

.noscroll {
    overflow: hidden;
    position: fixed;
}

.digest-address-link {
    margin-top: 10px;
    color: hsl(0deg 0% 60%);
    font-size: 12px;
    text-align: center;
}

.normal {
    font-weight: normal;
}

.navbar {
    margin-bottom: 0;
}

.header {
    position: relative;

    padding: 15px 0;
    height: 29px;

    background-color: hsl(0deg 0% 100%);
    box-shadow: 0 0 4px hsl(0deg 0% 0% / 10%);

    z-index: 100;
}

.navbar.footer .nav {
    > li {
        line-height: 56px;

        > a {
            padding-top: 0;
            padding-bottom: 0;
        }
    }
}

.push {
    height: 56px;
}

/* The API tabbed content tends to have a lot of code blocks,
   which look nicer against a different background */
.api-center .code-section {
    .blocks {
        background-color: hsl(0deg 0% 98%);
    }

    & ul.nav {
        & li.active {
            background-color: hsl(0deg 0% 98%);
            border-bottom: 1px solid hsl(0deg 0% 98%);
        }
    }
}

.digest-container {
    padding-top: 100px;
}

.digest-email-container {
    display: block;
    margin: 0 auto !important;
    max-width: 700px;
    padding-bottom: 30px;
}

.digest-email-html {
    padding: 20px;
    background-color: hsl(0deg 0% 100%);
    border-radius: 5px;
}

.app.help {
    display: inline-flex;

    box-shadow: 0 -20px 50px hsl(0deg 0% 0% / 4%);
    overflow: auto;

    color: hsl(0deg 0% 27%);

    .hamburger {
        display: none;
    }
}

.help {
    .app-main {
        padding: 0;
        margin-top: 59px;
    }

    /* Markdown processor generates lots of spurious <p></p> */
    & p:empty {
        margin: 0;
    }

    .sidebar {
        width: 300px;
        z-index: 1;
        /* 100vh - navbar - paddingTop - paddingBottom - bottomNav */
        height: calc(100vh - 59px);

        border-right: 1px solid hsl(219deg 10% 97%);
        overflow: auto;

        background-color: hsl(153deg 32% 55%);
        color: hsl(0deg 0% 100%);

        -webkit-overflow-scrolling: touch;

        --help-sidebar-padding: 20px;
        --help-sidebar-indent: 12px;

        .content {
            padding: 10px var(--help-sidebar-padding);
        }

        & h1 {
            font-weight: 400;
            font-size: 1.25em;
            line-height: 1.5;
            margin-bottom: 0;

            &.home-link {
                font-size: 1em;
                margin-top: 20px;
                margin-bottom: 17px;

                & a::before {
                    display: inline-block;
                    font: normal normal normal 14px/1 FontAwesome;
                    font-size: inherit;

                    content: "\f0d9";
                    margin-right: 10px;
                }
            }
        }

        & h1,
        h2,
        h3 {
            &:not(:first-of-type) {
                margin-top: 0;
            }

            & a {
                color: inherit;
                display: block;

                /* Extend to entire width of sidebar, not just link area */
                margin-left: calc(0px - var(--help-sidebar-padding));
                margin-right: calc(0px - var(--help-sidebar-padding));
                padding-left: calc(var(--help-sidebar-padding));
                padding-right: calc(var(--help-sidebar-padding));
            }
        }

        & h2 {
            font-weight: 400;
            font-size: 1.1em;
            line-height: 1.05;
            margin-bottom: 5px;
        }

        &.slide h2 {
            cursor: pointer;

            &::before {
                display: block;
                font: normal normal normal 14px/1 FontAwesome;
                font-size: inherit;

                content: "\f107";
                margin-right: 5px;
                float: right;

                opacity: 0.5;
            }
        }

        & ul {
            margin: 5px 0 10px var(--help-sidebar-indent);
        }

        &.slide ul {
            margin-left: 19px;
            display: none;
        }

        & li {
            list-style-type: none;
            font-size: 0.95em;
            font-weight: 400;
            line-height: 1.7;

            cursor: pointer;

            & a {
                color: inherit;
                display: block;

                /* Extend to entire width of sidebar, not just link area */
                margin-left: calc(
                    0px - var(--help-sidebar-padding) -
                        var(--help-sidebar-indent)
                );
                margin-right: calc(0px - var(--help-sidebar-padding));
                padding-left: calc(
                    var(--help-sidebar-padding) + var(--help-sidebar-indent)
                );
                padding-right: calc(var(--help-sidebar-padding));
            }
        }

        & a {
            &.highlighted {
                background-color: hsl(152deg 40% 42%);

                /* Don't show the focus outline for the highlighted page. */
                outline: 0;
            }
        }
    }
}

.help .markdown {
    background-color: hsl(0deg 0% 100%);
    width: calc(100vw - 300px);
    height: calc(100vh - 59px);
}

.help-center ol,
.portico-landing.integrations ol {
    margin-left: 0;
}

.title {
    font-family: Helvetica, sans-serif;
    font-size: 100px;
    font-weight: bold;
    margin-top: 50px;
    margin-bottom: 60px;
}

.digest-page-title {
    text-align: center;
    font-weight: 400;
}

.thanks-page div {
    text-align: center;
}

.lead {
    font-weight: bold;
}

.pitch {
    width: 600px;
    max-width: 100%;
}

.help-inline {
    font-weight: 400;
    font-size: 0.9rem;

    &.text-error {
        color: hsl(1.1deg 44.7% 50.4%);
    }
}

a.title {
    color: hsl(0deg 0% 0%);

    &:hover {
        color: hsl(0deg 0% 50%);
        text-decoration: none;
    }
}

.fakecontrol {
    padding-top: 5px;
    font-weight: bold;
}

img.screenshot {
    /* This makes it so screenshots are still shown
    even if they are larger than their span. */
    max-width: 100%;
}

#pw_strength {
    /* Same width as a Bootstrap default text <input> with padding */
    width: 220px;
    height: 8px;
}

#registration #pw_strength {
    width: 325px;
    margin: 7px auto 0;
}

.def::before {
    content: " - ";
}

.landing-page {
    padding: 2em 0;

    & h2,
    h4 {
        font-weight: lighter;
    }

    & p {
        font-size: 120%;
    }
}

.platform-icon {
    width: 33%;
}

.portico-page h1 {
    font-weight: 300;
}

label.text-error {
    display: inline;

    padding-left: 5px;
}

input.text-error {
    border-color: hsl(0deg 100% 50%);
    outline-color: hsl(0deg 100% 50%);
}

.portico-container {
    position: relative;
    /* To adjust for flexible footer height we do 2 things:
      - Make the `portico-container` expand to full page height.
      - Fill the empty space with `portico-wrap`. */
    display: flex;
    flex-direction: column;
    height: 100%;

    .portico-wrap {
        flex: 1 0 auto;
    }

    .if-zulip-electron {
        display: none;
    }
}

/* detect if the platform is `ZulipDesktop` and if so, hide this tag! */
.portico-container[data-platform="ZulipElectron"] .if-zulip-electron {
    display: block;
}

.header-main {
    .logo {
        display: block;
        text-decoration: none;
        position: relative;
        line-height: 0.8;

        & svg {
            vertical-align: -5px;
        }

        & a,
        a:focus,
        a:hover {
            text-decoration: none;
            color: hsl(0deg 0% 20%);
        }

        .light {
            font-size: 1.2rem;
            font-weight: 400;
            color: hsl(0deg 0% 20%);
            opacity: 0.7;
        }
    }

    .portico-logo {
        height: 28px;
        width: auto;
        padding: 6px 0;
    }
}

.portico-header {
    .dropdown {
        position: relative;
        display: inline-block;

        & ul {
            display: none;
            position: absolute;
            right: 0;
            margin: 10px 0 0;
            list-style-type: none;
            width: fit-content;
            background-color: hsl(0deg 0% 100%);
            padding: 5px 0;
            border-radius: 4px;
            border: 1px solid hsl(0deg 0% 87%);
            box-shadow: 0 2px 5px hsl(0deg 0% 0% / 10%);

            &::before {
                content: "\25B2";
                position: absolute;
                top: -4px;
                right: 9px;
                font-size: 0.5em;
                color: hsl(0deg 0% 87%);
                line-height: 0;
                transform: scale(1.8, 1);
            }

            & li {
                display: list-item;
                margin: 0;
                padding: 3px 10px;
                text-align: left;
                opacity: 1;
                cursor: pointer;

                &:hover {
                    background-color: hsl(190deg 10% 90%);
                    transition: none;
                }

                & a {
                    display: block;
                    margin: 2px 0;
                    padding: 0;
                    transition: none;
                    font-size: 0.9em;
                    font-weight: 400;
                    color: hsl(0deg 0% 27%);
                }

                &:hover a {
                    background-color: transparent;
                }

                & a i {
                    margin-right: 5px;
                }

                &.nav-header {
                    background-color: transparent;
                    cursor: default;
                    font-size: 14px;
                }
            }

            &.dropdown-list {
                margin-top: 3px;
                margin-right: 3px;
            }
        }

        &.show ul {
            display: block;
        }
    }

    .dropdown-pill {
        border: 1px solid hsl(0deg 0% 0% / 20%);
        border-radius: 4px;
        margin-left: 10px;
        font-weight: 400;
        cursor: pointer;

        .realm-name {
            display: inline-block;
            vertical-align: top;
            margin: 0 5px 0 -4px;
            padding: 1px 0 1px 5px;
            font-size: 0.9em;
            font-weight: 600;
            line-height: 1.6;
        }

        .realm-name i.fa {
            position: relative;
            top: -2px;
            font-size: 0.6em;
            margin-left: 5px;
            opacity: 0.5;
            transition: all 0.2s ease;
        }

        &:hover .realm-name i.fa {
            opacity: 1;
        }

        .header-realm-icon {
            width: 26px;
            height: 26px;
            vertical-align: top;
            border-radius: 4px;
        }
    }
}

.portico-page-container .portico-header .dropdown-pill .realm-name {
    margin-left: -3px;
}

.app {
    width: 100%;
    z-index: 99;
}

.devlogin_subheader {
    margin-top: 10px;
    margin-bottom: 20px;
    padding-top: 0;
    text-align: center;
    font-size: 16px;
}

.table.table-striped {
    background-color: hsl(0deg 0% 100%);
    box-shadow: 0 0 4px hsl(0deg 0% 0% / 10%);
}

.team-profiles {
    /* Compensate for gutter width */
    margin: -10px;
    margin-bottom: 3px;
}

.team {
    .profile {
        .profile-name {
            font-weight: 600;
        }

        .profile-role {
            opacity: 0.5;
            text-transform: uppercase;
            font-size: 0.8em;
            font-weight: 400;
        }
    }

    .bdfl {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;

        .profile-picture {
            flex: 0 auto;
            width: 200px;
            margin: 10px;

            > img {
                height: auto;
                border-radius: 5px;
            }
        }

        .profile-information {
            flex: 1;
            /* Wrap when screen is small to prevent very short line */
            min-width: 300px;
            font-size: 1.4em;
            margin: 10px 10px 0;
        }

        .profile-description {
            margin-top: 5px;
            font-weight: 400;
            font-size: 0.8em;
            opacity: 0.8;

            & p {
                /* Avoid double-applying the 1.2em font-size here */
                font-size: 1em;
            }
        }
    }

    & input {
        display: none;

        &:checked + label {
            border: 1px solid hsl(0deg 0% 93%);
            border-top: 2px solid hsl(80deg 61% 50%);
            border-bottom-color: hsl(0deg 0% 100%);
        }
    }

    & label {
        font-size: initial;
        display: inline-block;
        padding: 10px;
        border: 1px solid transparent;
        margin: 0 0 -1px;

        &:hover {
            cursor: pointer;
        }
    }
}

.contributors-list {
    margin-left: -40px;
    width: calc(100% + 80px);
}

.contributors {
    display: none;

    .person {
        box-sizing: border-box;
        padding: 10px;
        border: 1px solid hsl(0deg 0% 93%);
        border-radius: 4px;
        transition: all 0.3s ease;

        & a {
            color: inherit;
        }

        &:hover {
            border: 1px solid hsl(0deg 0% 73%);
        }

        .avatar {
            width: 60px;
            text-align: center;
            display: inline-block;
            vertical-align: top;
        }

        .info {
            width: 50%;
            text-align: left;
            display: inline-block;
            vertical-align: top;
            margin-left: 10px;
        }
    }
}

/* Activated .contributors */
input#total:checked ~ #tab-total,
input#server:checked ~ #tab-server,
input#desktop:checked ~ #tab-desktop,
input#mobile:checked ~ #tab-mobile,
input#python-zulip-api:checked ~ #tab-python-zulip-api,
input#zulip-js:checked ~ #tab-zulip-js,
input#zulipbot:checked ~ #tab-zulipbot,
input#terminal:checked ~ #tab-terminal {
    display: block;

    .contributors-grid {
        padding-top: 5px;
        display: grid;
        grid-gap: 5px;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    }
}

.avatar_img {
    width: auto;
    height: auto;
    max-width: 80%;
    max-height: 80%;
    border-radius: 20%;
}

.tab-loading,
.last-updated {
    color: hsl(0deg 0% 67%);
    font-size: 0.9em !important;
    padding-top: 30px;
    text-align: center;
}

.history .sponsors {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;

    .sponsor-picture img {
        height: 170px;
        margin: 0 20px;
        pointer-events: none;
    }
}

.login-page-header {
    width: 100%;
}

.login-page {
    text-align: center;

    .alert {
        width: 320px;
        margin: auto;
        margin-top: -30px;
        margin-bottom: 15px;
        text-align: center;
    }
}

.register-form {
    display: inline-block;
    text-align: center;
}

.register-button {
    margin-left: 10px;
}

.new-organization-button {
    margin-top: 10px;
}

input.new-organization-button {
    display: block;
    margin-left: auto;
    margin-right: auto;
}

.login-form {
    margin: auto;
    /* plus input padding. */
    width: calc(300px - -28px);
    margin-bottom: 10px;
}

.login-form,
.register-form {
    .controls {
        margin-right: 10px;
    }
}

.login-social {
    max-width: 100%;
    min-width: 300px;
    margin: auto;
    text-align: center;
    margin-top: 10px;
}

.app-main,
.header-main {
    min-width: 350px;
    margin: 0 auto;
    padding: 0 20px;
    position: relative;
}

.hello-main {
    max-width: none;
    min-width: 0;
    padding: 0 !important;
}

.top-links {
    text-align: right;

    & a {
        display: inline-block;
        color: hsl(0deg 0% 100%);
        padding: 2px 7px 1px 8px;
        font-weight: 600;
        font-size: 16px;
        transition: all 0.2s ease-in;
        border-radius: 4px;

        &:hover {
            text-decoration: none;
            background-color: hsl(0deg 0% 100%);
            color: hsl(170deg 50% 40%);
        }
    }
}

.centered-button {
    text-align: center;
}

/* -- password reset container -- */
.password-reset {
    display: inline-block;
    text-align: left;
    width: 328px;

    & form {
        margin: 0;
    }

    #pw_strength {
        width: 328px;
        margin-top: 20px;
    }

    .pitch {
        width: auto;
    }

    .input-group {
        margin: 15px 0;

        & input[type="text"],
        input[type="password"] {
            width: calc(100% - 14px);
        }

        #pw_strength {
            width: 100%;
        }

        &.m-t-30 {
            margin-top: 30px;
        }
    }

    & p {
        margin: 0;
    }

    .progress {
        margin: 0;
    }

    #email-section .fakecontrol {
        display: inline-block;
        margin: 0;
    }
}

.input-group {
    &.margin {
        margin: 10px 0;
    }

    .progress {
        margin: 0;
        margin-top: 5px;
        display: inline-block;
    }

    /* --- new settings styling --- */
    & input[type="radio"],
    input[type="checkbox"] {
        margin: 0 10px 0 0;
    }

    & input[type="radio"] {
        position: relative;
        top: 8px;
    }

    & label {
        margin: 0;
        padding: 5px 0;

        &.inline-block {
            /* eyeballing off-centered aesth. */
            margin-top: 1px;
        }
    }

    &.radio {
        margin-left: 25px;
    }

    &.grid {
        padding: 10px 0;
        border-bottom: 1px solid hsl(0deg 0% 87%);

        & label.inline-block {
            width: 200px;
        }
    }
}

.center-container {
    min-height: calc(100vh - 94px);
    min-height: 700px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
}

#registration-email {
    & label {
        float: left;
        padding-top: 5px;
        width: 100%;
        display: block;
        margin: 0;
        text-align: left;
    }
}

.center-block {
    text-align: left;
    display: inline-block;

    .pitch {
        width: 100%;
        margin-bottom: 20px;
    }

    .controls {
        margin: 0;
        text-align: left;
    }

    #send_confirm input[type="text"] {
        margin-top: 20px;
    }

    .button {
        margin-top: 20px;
        padding: 5px 10px;
        border-radius: 2px;
        font-size: 16px;
        font-weight: 300;
    }
}

.error_page {
    min-height: calc(100vh - 290px);
    height: 100%;
    background-color: hsl(163deg 42% 85%);
    font-family: "Source Sans 3", sans-serif;
}

.error_page .container {
    padding: 20px 0;
}

.error_page .row-fluid {
    margin-top: 60px;
}

.error_page img {
    display: block;
    clear: right;
    margin: 0 auto;
    max-width: 500px;
    width: 100%;
}

.error_page .errorbox {
    margin: auto;
    border: 2px solid hsl(163deg 43% 46%);
    max-width: 500px;
    background-color: hsl(0deg 0% 100%);
    box-shadow: 0 0 4px hsl(163deg 43% 46%);
    font-size: 18px;

    &.config-error {
        max-width: 750px;
    }
}

.error_page p {
    color: hsl(0deg 0% 20%);
}

.error_page .errorcontent {
    text-align: left;
    padding: 40px 40px 30px;
}

.error_page .lead {
    color: hsl(163deg 49% 44%);
    font-size: 35px;
    margin-bottom: 20px;
    line-height: normal;
}

.hourglass-img {
    width: initial !important;
    margin-bottom: 25px !important;
}

@media (width <= 800px) {
    .app.help {
        .markdown {
            width: 100vw;

            .content {
                max-width: none;
                margin-left: 50px;
            }
        }

        .hamburger {
            display: block;
            position: fixed;
            top: 70px;
            left: 9px;
            fill: hsl(0deg 0% 100%);
            z-index: 2;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .sidebar {
            position: fixed;
            top: 59px;
            right: calc(100vw - 50px);
            width: 100%;
            min-width: unset;
            height: calc(100vh - 59px);
            pointer-events: none;
            overflow: hidden;
            transform: translateX(0);
            transition: all 0.3s ease;
        }

        .sidebar.show {
            pointer-events: initial;
            transform: translateX(calc(100% - 50px));
            overflow: auto;

            .content {
                visibility: visible;
            }

            + .hamburger {
                transform: translateX(calc(100vw - 50px));
            }

            ~ .markdown {
                filter: brightness(0.7);
            }
        }
    }

    .app-main,
    .header-main {
        min-width: auto;
    }

    .app-main {
        padding: 0;
    }

    .help .sidebar {
        .content:not(.show) {
            visibility: hidden;
        }

        &:not(.show) a.highlighted {
            background-color: transparent;
        }
    }
}

@media (width <= 767px) {
    body {
        padding: 0 !important;
    }

    .input-large {
        display: block !important;
        width: 100% !important;
        min-height: 30px !important;
        margin: 0 !important;
        padding: 4px 6px !important;
        line-height: 20px !important;
        box-sizing: border-box !important;
        margin-top: 10px !important;
        margin-bottom: 10px !important;
    }

    .line-break-desktop {
        display: none;
    }

    .contributors-list {
        width: 100%;
        margin-left: 0;
    }
}

@media (max-height: 600px) {
    .password-container {
        margin-top: 10px;
    }
}

@media (width <= 558px) {
    .team {
        .bdfl {
            .profile-name,
            .profile-role {
                text-align: center;
            }
        }
    }
}

@media (width <= 500px) {
    .app.help {
        .sidebar {
            top: 39px;
            height: calc(100vh - 39px);
        }

        .hamburger {
            top: 50px;
        }
    }

    .help .app-main {
        margin-top: 39px;
    }

    .help .markdown {
        height: calc(100vh - 39px);
    }

    .error_page .lead {
        font-size: 1.5em;
        margin-bottom: 10px;
    }

    .brand.logo .light {
        display: none;
    }

    .center-container {
        display: block;
    }

    .header {
        padding: 4px 0 6px;
    }

    .header-main {
        max-width: 100vw;
        padding: 0 10px;
    }
}

.emoji {
    height: 25px;
    width: 25px;
    vertical-align: text-bottom;
}

label.label-title {
    font-weight: 600;
}

.inline-block {
    display: inline-block;
    vertical-align: top;
}

.float-left {
    float: left;
}

.float-right {
    float: right;
}

.documentation-footer {
    font-size: 0.85rem;
    opacity: 0.8;
}

#devtools-wrapper {
    text-align: right;
}

#devtools-registration {
    float: left;

    & form {
        display: inline;
    }
}

#devtools-page {
    max-width: 800px;
    margin: 0 auto;
}

.portico-page.error {
    padding-bottom: 0;
}

.portico-page.error .portico-page-container {
    padding: 0;
}

#third-party-apps {
    margin-top: 20px;
    padding-right: 10px;
}

.api-argument {
    .api-argument-name {
        font-family: "Source Code Pro", monospace;

        .api-argument-hover-link i.fa {
            opacity: 0;
            font-size: 0.9em;
        }

        &:hover .api-argument-hover-link i.fa {
            opacity: 1;
            color: hsl(0deg 0% 0%);
            cursor: pointer;
        }
    }

    .api-field-type {
        text-transform: lowercase;
        font-weight: 600;
        font-size: 14px;
    }

    .api-argument-example-label {
        font-style: italic;
    }

    .api-argument-required {
        text-transform: uppercase;
        font-weight: 600;
        font-size: 12px;
        color: hsl(14deg 75% 60%);
    }

    .api-argument-optional {
        text-transform: uppercase;
        font-weight: 400;
        font-size: 12px;
        color: hsl(0deg 0% 47%);
    }

    .api-argument-deprecated {
        text-transform: uppercase;
        font-weight: 600;
        font-size: 12px;
        color: hsl(0deg 50% 60%);
    }
}

.api-field-type {
    color: hsl(176deg 46.4% 41%);
}

.desktop-redirect-box {
    text-align: center;

    .copy-token-info {
        font-weight: normal;
    }

    #desktop-data {
        padding: 13px 12px 12px;
        font-family: "Source Code Pro", monospace;
    }
}

.desktop-redirect-image {
    margin-bottom: 20px;
}

.unsupported_browser_page {
    padding-bottom: 80px;
}

#navbar-custom-message {
    font-size: 1rem;
    background: linear-gradient(
        145deg,
        hsl(191deg 56% 55%),
        hsl(169deg 65% 42%)
    );
    color: hsl(0deg 0% 100%);
    font-weight: 600;
    text-align: center;
    position: relative;
    top: 0;
    padding: 10px;
    border-bottom: 1px solid hsl(177deg 52% 55%);
    z-index: 5;

    & a {
        color: hsl(0deg 0% 100%);
        text-decoration: underline;
    }
}

~~~
#### settings.css ####
~~~
/* The height of the settings header (including tab switcher). */
$settings_header_height: 45px;
/* The width of the settings sidebar. */
$settings_sidebar_width: 250px;

label {
    margin: 0;

    .fa-question-circle-o {
        left: 2px;
    }
}

label,
h4,
h3,
/* We need settings-section-title here because some legacy settings
   widgets use a <div> with this class for their heading. */
.settings-section-title {
    & a {
        color: inherit;
    }

    .fa-question-circle-o {
        top: 1px;
        /* This should match .settings-info-icon. */
        opacity: 0.6;
        position: relative;

        &:hover {
            opacity: 1;
        }
    }

    .fa-info-circle {
        top: 1px;
        position: relative;
    }
}

/* TODO: This should ideally be added to help_link_widget.hbs,
   allowing us to deduplicate at least the opacity CSS with the
   fa-question-circle-o logic above. */
.settings-info-icon {
    padding-left: 3px;
    opacity: 0.6;

    &:hover {
        opacity: 1;
    }
}

h3,
.settings-section-title {
    .fa-question-circle-o {
        left: 5px;
    }
}

.new-style {
    .block {
        display: block;
    }

    .center-block {
        margin: 0 auto;
    }

    .center {
        text-align: center;
    }

    .w-200 {
        width: 200px;
    }

    .grid {
        & label {
            min-width: 200px;
        }

        .warning {
            display: inline-block;
            vertical-align: top;
            width: 150px;
            padding: 5px 10px;
            text-align: left;
        }
    }

    #account-settings,
    #profile-field-settings {
        .grid {
            & label {
                min-width: 120px;
            }

            .warning {
                display: block;
                width: calc(100% - 20px - 5px);
                text-align: right;
            }
        }
    }

    .warning {
        #pw_strength {
            width: 140px;
            height: 8px;
            margin: 6px 0 0;
        }
    }

    .button {
        & ul {
            text-align: left;
        }
    }
}

.profile-settings-form {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap-reverse;
}

.profile-main-panel {
    margin-right: 20px;
}

.profile-side-panel {
    margin-right: 10px;
}

#admin_profile_fields_table {
    & th.display,
    td.display_in_profile_summary_cell {
        text-align: center;
    }
}

.user-details-title {
    display: inline-block;
    min-width: 80px;
    font-weight: 600;
    padding-right: 5px;
}

.user-avatar-section {
    .inline-block {
        box-shadow: 0 0 10px hsl(0deg 0% 0% / 10%);
    }
}

#change_password_modal,
#change_email_modal {
    max-width: 480px;
}

#change_email_modal {
    #change_email_form {
        margin: 0;
    }
}

.disabled_setting_tooltip {
    cursor: not-allowed;
}

#account-settings .deactivate_realm_button {
    margin-left: 10px;
}

#change_email_button,
#user_deactivate_account_button,
.deactivate_realm_button {
    &:disabled {
        pointer-events: none;
    }
}

.admin-realm-description {
    height: 16em;
    width: 100%;
    max-width: 500px;
    box-sizing: border-box;
}

.side-padded-container {
    padding: 0 20px;
}

.setting_notification_sound,
.play_notification_sound {
    display: inline;
    margin-right: 4px;

    & i {
        font-size: 22px;
        cursor: pointer;
    }
}

.setting_notification_sound {
    text-transform: capitalize;
}

.table {
    & tbody {
        border-bottom: 1px solid hsl(0deg 0% 87%);
    }
}

.wrapped-table {
    word-break: break-word;
    word-wrap: break-word;
    white-space: pre-wrap;
    white-space: normal;
}

.table-condensed td {
    vertical-align: middle;
}

#settings_content {
    & table + .progressive-table-wrapper table tr.user_row td:first-of-type {
        width: 20%;
    }

    /* Limit the actions column to not using excessive width */
    .admin-table-wrapper table.admin_profile_fields_table tr .actions {
        width: 11%;
    }
}

#uploaded_files_table > tr > td:nth-of-type(1),
.upload-file-name {
    width: 43%;
    word-break: break-all;
}

.upload-mentioned-in,
.upload-date {
    word-break: normal;
}

#linkifier-settings {
    #linkifier_pattern,
    #linkifier_format_string {
        width: calc(100% - 10em - 6em);
    }
}

#playground-settings {
    #playground_pygments_language,
    #playground_name,
    #playground_url_prefix {
        width: calc(100% - 10em - 6em);
    }
}

td .button {
    margin: 2px 0;
    box-shadow: none;
}

#language_selection_modal {
    & table {
        width: 90%;
        margin-top: 20px;
        border-collapse: separate;
    }

    & td {
        padding-top: 1px;
    }
}

.settings-section {
    display: none;
    width: calc(100% - 40px);
    margin: 20px;

    &.show {
        display: block;
    }

    & form {
        margin: 0;
    }

    .no-padding {
        padding: 0;
    }

    .settings-section-title {
        font-size: 1.4em;
        font-weight: 500;
        margin: 10px 0;

        &.transparent {
            background-color: transparent;
            color: inherit;
        }
    }

    .table-sticky-headers th {
        position: sticky;
        top: 0;
        z-index: 1;
    }

    #admin_page_users_loading_indicator,
    #attachments_loading_indicator,
    #admin_page_deactivated_users_loading_indicator,
    #admin_page_bots_loading_indicator {
        margin: 0 auto;
    }

    .loading_indicator_text {
        font-size: 12px;
        font-weight: 400;
        vertical-align: middle;
        line-height: 20px;
        display: inline-block;
        float: none;
        margin-top: 9px;
    }

    .loading_indicator_spinner {
        width: 30%;
        height: 20px;
        margin-top: 7px;
        vertical-align: middle;
        display: inline-block;
    }

    .inline {
        display: inline !important;
    }

    /* Messy implementation of buttons with text and a pencil icon in them
       having spacing before the pencil icon. */
    & button.btn-link i.fa-pencil,
    button[data-dismiss="modal"] i.fa-pencil,
    .dropdown-toggle i.fa-pencil {
        margin-left: 3px;
    }

    .hidden-email {
        font-style: italic;
    }

    /* Originally the icon inherits the color of label, but when the setting
    is disabled, the color of the label is changed and thus the icon becomes
    too light. So, we set the color explicitly to original color of label to
    keep the color of the icon same even when the setting is disabled. */
    #id_realm_enable_spectator_access_label a {
        color: hsl(0deg 0% 20%);
    }

    .settings_select,
    .dropdown-list-widget .dropdown-toggle {
        height: 30px;
        min-width: 325px;
        max-width: 100%;
    }
}

.settings_select {
    padding: 4px 6px;
    color: hsl(0deg 0% 33%);
    border-radius: 4px;
    border: 1px solid hsl(0deg 0% 80%);
    cursor: pointer;
    background-color: hsl(0deg 0% 100%);

    &:disabled {
        cursor: not-allowed;
        background-color: hsl(0deg 0% 93%);
    }
}

.settings_text_input {
    width: 206px;
}

#admin-user-list,
#admin-bot-list {
    .table tr:first-of-type td {
        border-top: none;
    }
}

.user_role {
    min-width: 95px;
}

.button,
.input-group {
    margin: 0 0 20px;
}

.input-group {
    /* Class to use when the following input-group is related and should
       appear just after this element. Normally the margin is 20px, but
       for related settings, we set it to 10px. */
    &.thinner {
        margin-bottom: 10px;
    }

    & label.checkbox + label {
        cursor: pointer;
    }
}

.no-margin {
    margin: 0;
}

input[type="checkbox"] {
    + .inline-block {
        margin-left: 10px;
    }

    .inline-block {
        margin: -2px 0 0;
    }
}

.allow-subdomains,
.new-realm-domain-allow-subdomains {
    margin: 0 !important;
}

.realm_domains_info {
    margin-bottom: 0;
}

.admin-realm-form {
    & h3 {
        margin-bottom: 10px;
    }

    .subsection-header h3 {
        display: inline;
    }
}

.display-settings-form,
.notification-settings-form {
    .subsection-header h3 {
        display: inline-block;
    }
}

#stream-specific-notify-table .unmute_stream {
    position: relative;
    left: 3px;
    top: 2px;

    &:hover {
        color: hsl(0deg 0% 20%);
        cursor: pointer;
    }
}

.organization-settings-parent > div:first-of-type {
    margin-top: 10px;
}

#id_org_profile_preview {
    margin-bottom: 20px;
    display: inline-flex;
    justify-content: space-evenly;
    align-items: center;
}

.inline-block.organization-permissions-parent div:first-of-type {
    margin-top: 10px;
}

.language_selection_widget {
    .title {
        margin-bottom: 3px;
    }

    .language_selection_button {
        text-decoration: none;
        color: hsl(0deg 0% 20%);

        .fa.fa-pencil {
            margin-left: 5px;
        }
    }
}

.remove-attachment {
    margin-right: 5px !important;
    font-size: 1.1em !important;
    padding-left: 0 !important;
}

#download_attachment {
    padding-left: 0;
    border-left: 0;
}

.remove-alert-word {
    margin-top: 1px;
}

.alert_word_status_text {
    word-break: break-word;
}

.alert-notification {
    display: inline-block;
    vertical-align: top;
    height: auto !important;
    width: auto !important;

    background-color: transparent;
    border-radius: 4px;
    margin-top: 14px;
    margin-left: 10px;
    color: hsl(156deg 30% 50%);
    padding: 3px 10px;

    &:not(:empty) {
        border: 1px solid hsl(156deg 30% 50%);
    }

    &.alert-error {
        color: hsl(2deg 46% 68%);
        border-color: hsl(2deg 46% 68%);
    }

    .loading_indicator_spinner {
        width: 13px;
        height: 20px;
        margin: 0;
    }

    /* make the spinner green like the text and box. */
    .loading_indicator_spinner svg path {
        fill: hsl(178deg 100% 40%);
    }

    .loading_indicator_text {
        margin-top: 0;
        font-size: inherit;
        vertical-align: top;
    }

    & img {
        margin-right: 6px;
        vertical-align: middle;
        margin-top: -2px;
    }
}

#profile-field-settings #admin-add-profile-field-status {
    margin-top: 4px;
}

#add-custom-profile-field-btn {
    float: right;
    margin-top: 4px;
}

#user-notification-settings {
    .notification-table {
        & th,
        td {
            text-align: center;
            vertical-align: middle;
            cursor: default;

            .stream-privacy span.hashtag,
            .filter-icon i {
                padding-right: 0;
            }

            & label {
                cursor: default;
            }
        }

        & td:first-child {
            text-align: left;
            font-weight: bold;
            word-break: break-all;
        }
    }
}

#profile-settings {
    .custom-profile-fields-form .custom_user_field label,
    .full-name-change-container label,
    .timezone-setting-form label {
        min-width: fit-content;
    }

    .alert-notification.custom-field-status,
    .alert-notification.full-name-status,
    .alert-notification.timezone-setting-status {
        padding-top: 0;
        padding-bottom: 0;
        margin-top: 0;
        padding-left: 0;
        margin-left: 5px;
        border: none;
    }
}

.control-label-disabled {
    color: hsl(0deg 0% 82%);

    &.enabled {
        color: hsl(0deg 0% 20%);
    }
}

.admin-realm-message-retention-days {
    width: 5ch;
    text-align: right;
}

#show-add-user-group-modal {
    margin-bottom: 10px;
}

#add-user-group-form {
    margin: 0;

    /* This 14px is the border and padding of the input element */
    #user_group_description {
        width: calc(100% - 14px);
    }
}

.add-new-export-box {
    margin: 10px 0;
}

.add-new-default-stream-box {
    & input[type="text"] {
        padding: 6px;
    }
    margin-bottom: 15px;
}

#add-custom-emoji-modal {
    & form {
        margin: 0;
    }

    & input[type="text"] {
        padding: 6px;
    }

    .emoji_name_input {
        margin-top: 10px;
    }

    #emoji-file-name {
        font-size: 14px;
        white-space: nowrap;
        height: 1rem;
        font-style: italic;
        color: hsl(0deg 0% 67%);
    }

    #emoji_preview_text {
        margin-top: 6px;
    }
}

#emoji_file_input_error {
    vertical-align: middle;
}

.add-new-linkifier-box,
.add-new-playground-box {
    & button {
        margin-left: calc(10em + 20px) !important;
    }
    margin-bottom: 15px;

    .checkbox {
        margin-top: 5px;
    }
}

.grey-box .wrapper {
    margin: 10px 0;
}

.admin_profile_fields_table,
.edit_profile_field_choices_container,
.profile_field_choices_table {
    .movable-profile-field-row {
        cursor: move;

        .fa-ellipsis-v {
            color: hsl(0deg 0% 75%);
            position: relative;
            top: 1px;

            + i {
                margin-right: 5px;
            }
        }
    }
}

#admin-linkifier-pattern-status,
#admin-linkifier-format-status {
    margin: 20px 0 0;
}

.progressive-table-wrapper {
    position: relative;
    max-height: calc(95vh - 220px);
    overflow: auto;
    width: 100%;
}

#admin-default-streams-list .progressive-table-wrapper {
    max-height: calc(95vh - 280px);
}

#bot-settings .add-a-new-bot {
    margin-bottom: 2px;
}

.bots_list {
    display: none;
    list-style-type: none;
    margin-left: 0;

    .image {
        vertical-align: top;
    }

    .name {
        font-weight: 600;
        font-size: 1.1rem;
        margin: 7px 5px;

        overflow: hidden;
        line-height: 1.3em;
        text-overflow: ellipsis;
        white-space: pre;
    }

    .regenerate_bot_api_key {
        position: relative;
        margin-left: 5px;
        color: hsl(0deg 0% 67%);
        transition: all 0.3s ease;

        &:hover {
            color: hsl(0deg 0% 27%);
        }
    }

    .edit-bot-buttons {
        padding-top: 5px;

        & button {
            background-color: transparent;
        }

        .btn {
            padding: 4px;
        }

        .sea-green {
            color: hsl(177deg 70% 46%);
        }

        .blue {
            color: hsl(203deg 77% 56%);
        }

        .danger-red {
            color: hsl(0deg 56% 73%);
        }

        .copy-gold {
            color: hsl(51deg 90% 50%);
        }

        .purple {
            color: hsl(278deg 62% 68%);
        }
    }

    .bot-information-box {
        position: relative;
        display: inline-block;
        width: calc(50% - 10px);
        max-height: 220px;
        margin: 5px;

        border-radius: 4px;
        box-sizing: border-box;

        overflow: auto;

        .details {
            display: inline-block;
            width: calc(100% - 75px);
        }
    }

    & img.avatar {
        margin: 10px 5px 0 10px;
        height: 50px;
        width: 50px;
        border-radius: 4px;
        vertical-align: top;
        box-shadow: 0 0 4px hsl(0deg 0% 0% / 10%);
    }

    .email,
    .type {
        margin-bottom: 5px;
    }

    .email .value,
    .api_key .api-key-value-and-button {
        display: block;
        margin-left: 0;
        word-wrap: break-word;
        word-break: break-all;
        white-space: normal;
    }

    .api_key .api-key-value-and-button {
        font-family: "Source Code Pro", monospace;
        font-size: 0.85em;
        display: flex;
    }

    .bot_info {
        padding: 10px;
    }

    .field {
        text-transform: uppercase;
        font-weight: 600;
        color: hsl(0deg 0% 67%);
    }
}

#bots_lists_navbar .active a {
    background-color: hsl(0deg 0% 98%);
}

#inactive_bots_list .bot_info .reactivate_bot {
    margin-top: 5px;
}

.edit_bot_form {
    font-size: 100%;
    margin: 0;
    padding: 0;

    .buttons {
        margin: 10px 0 5px;
    }

    #current_bot_avatar_image {
        margin: 5px 0 8px;
    }

    .edit_bot_avatar_preview_text {
        display: none;
    }
}

#add_bot_preview_text {
    display: none;
}

.edit_bot_avatar_preview_image,
#add_bot_preview_image {
    height: 100px;
    width: 100px;
    margin: 2px 0 8px;
}

#add-alert-word {
    & form {
        margin-bottom: 4px;
    }

    & input {
        margin-bottom: 0;
    }
}

.admin-linkifier-form,
.admin-playground-form {
    & label {
        float: left;
        padding-top: 5px;
        width: 10em;
        text-align: right;
        margin-right: 20px;
    }
}

.admin-profile-field-form #custom_external_account_url_pattern input,
#edit-custom-profile-field-form-modal .custom_external_account_detail input {
    width: 70%;
}

#alert-words-table {
    margin: 0;

    & li {
        list-style-type: none;

        &.alert-word-item:first-child {
            background: none;
            margin-top: 8px;
        }
    }

    .alert_word_listing .value {
        word-wrap: break-word;
        word-break: break-all;
        white-space: normal;
    }

    .edit-attachment-buttons {
        position: absolute;
        right: 20px;
        top: 0;
    }
}

#change_password_modal {
    #change_password_container {
        margin: 0;
    }
}

#api_key_status {
    margin: 0 0 10px;
}

#download_zuliprc {
    color: hsl(0deg 0% 100%);
    text-decoration: none;
}

#realm_domains_table {
    margin: 0;
}

#api_key_form,
#change_password_modal {
    .password-div {
        position: relative;

        & input[type="text"] {
            margin-bottom: 10px;
        }

        .password_visibility_toggle {
            position: absolute;
            left: 194px;
            top: 32px;
            width: 14px;
            opacity: 0.6;

            &:hover {
                opacity: 1;
            }
        }
    }
}

.emojiset_choices,
.user_list_style_values {
    padding: 0 10px;
}

label.display-settings-radio-choice-label {
    border-bottom: 1px solid hsl(0deg 0% 0% / 20%);
    padding: 8px 0 10px;

    &:last-of-type {
        border-bottom: none;
    }

    & input[type="radio"] {
        position: relative;
        top: -2px;
        margin: 0 5px 0 0;
        width: auto;
        cursor: pointer;

        &:focus {
            outline: 1px dotted hsl(0deg 0% 20%);
            outline: 5px auto -webkit-focus-ring-color;
            outline-offset: -2px;
        }

        &:disabled {
            cursor: not-allowed;
        }

        &:checked + span {
            font-weight: 600;
        }
    }

    .right {
        float: right;
    }
}

.emojiset_choices {
    width: 350px;

    .emoji {
        height: 22px;
        width: 22px;
    }
}

$right_sidebar_width: 170px;
$option_title_width: 180px;

.user_list_style_values {
    max-width: calc($right_sidebar_width + $option_title_width);

    .preview {
        background-color: inherit !important;
        /* Match the 170px width of the right sidebar region for the name/status,
           doing something reasonable if the window shrinks. */
        width: calc(100% - $option_title_width);
        text-align: left;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow-x: hidden;
        overflow-y: visible;
        position: relative;
        height: 36px;

        .user-name-and-status-text {
            margin-top: -4px;
            display: flex;
            flex-direction: column;
        }

        .status-text {
            display: inline-block;
            opacity: 0.75;
            font-size: 90%;

            &:not(:empty) {
                margin-top: -3px;
            }
        }
    }
}

.open-user-form {
    min-width: initial !important;
}

#api_key_buttons {
    display: inline-flex;

    .regenerate_api_key {
        margin-right: 5px;
    }
}

.right.show .emoji_alt_code {
    font-size: 1.2em;
}

.invite-user-link i {
    text-decoration: none;
    margin-right: 5px;
}

#user-groups {
    .user-group {
        margin-bottom: 20px;
        padding: 10px;
        border-radius: 5px;

        & h4 {
            font-weight: normal;
            margin: 0;
            display: flex;
            align-items: center;
            justify-content: left;
        }

        & span[contenteditable] {
            display: inline-block;
            word-break: break-all;

            &:empty::before {
                opacity: 0.5;
                display: inline-block;
                content: attr(data-placeholder);
            }
        }

        & span[contenteditable]:focus,
        span[contenteditable="true"]:hover {
            border-bottom: 1px solid hsl(0deg 0% 80%);
            margin-bottom: -1px;
            outline: none;
        }

        .pill-container .input[contenteditable]:empty::after {
            content: attr(data-placeholder);
            opacity: 0.5;
        }
    }

    .user-group-status {
        margin-bottom: 10px;
    }

    & p {
        line-height: 2;
        margin: 0;
    }

    .spacer {
        margin: 0 2px;
    }

    .subscribers,
    .user-group h4 > .name {
        font-weight: bold;
    }

    .ntm {
        cursor: not-allowed;

        & h4 > .button {
            cursor: not-allowed;
            display: none;

            &:hover {
                border-color: hsl(4deg 56% 82%);
            }
        }
    }

    .save-status {
        background-color: transparent;
        padding: 2px 5px;
        border-radius: 4px;
        margin-left: 10px;
        border-style: solid;
        border-width: 1px;
        display: none;
        opacity: 0;
    }

    .checkmark {
        height: 12px;
    }

    .delete {
        margin-left: auto;
    }

    .save-instructions {
        display: none;
        opacity: 0;
        color: hsl(0deg 0% 20%);
        font-size: 0.9em;
    }
}

/* -- new settings overlay -- */
#settings_page {
    height: 95vh;
    width: 97vw;
    max-width: 1024px;
    margin: 2.5vh auto;
    overflow: hidden;
    border-radius: 4px;

    .time-limit-custom-input {
        width: 5ch;
        text-align: right;
    }

    .realm-time-limit-label {
        vertical-align: middle;
    }

    & h3 {
        font-size: 1.5em;
        font-weight: normal;
        line-height: 1.5;
    }

    & h5 {
        font-size: 1.2em;
        font-weight: normal;
        line-height: 1.2;
        margin: 10px 0;
    }

    .sidebar-wrapper {
        float: left;
        position: relative;
        width: $settings_sidebar_width;
        height: 100%;

        .tab-container {
            box-sizing: border-box;
            height: $settings_header_height;
            padding: 6px;
            border-bottom: 1px solid hsl(0deg 0% 87%);
        }
    }

    .sidebar {
        height: calc(100% - $settings_header_height);
        overflow-y: auto;
        border-right: 1px solid hsl(0deg 0% 93%);

        .header {
            height: auto;
            position: relative;
            width: calc(100% - 20px);
            padding: 10px;
            text-align: center;
            text-transform: uppercase;

            background-color: hsl(180deg 6% 93%);
            border-bottom: 1px solid hsl(0deg 0% 87%);
        }

        & ul {
            list-style: none;
            margin: 0;
            padding: 0;
        }

        & li {
            padding: 5px 0;
            outline: none;
            cursor: pointer;
            transition: all 0.2s ease;
            border-bottom: 1px solid hsl(0deg 0% 93%);

            &:last-of-type .text {
                border-bottom: none;
            }

            &.active {
                background-color: hsl(0deg 0% 93%);
                border-bottom: 1px solid transparent;
            }

            .text,
            .icon,
            .locked {
                display: inline-block;
                vertical-align: top;
            }

            .text {
                width: calc(100% - 90px);
                padding: 10px 12px 10px 0;
            }

            .icon {
                width: 18px;
                height: 18px;
                margin: 10px;
                text-align: center;

                font-size: 1.4em;
                color: hsl(0deg 0% 53%);

                background-size: cover;
                background-repeat: no-repeat;
            }

            .locked {
                width: 18px;
                height: 18px;
                margin: 14px 8px 6px;

                font-size: 1em;
                color: hsl(0deg 0% 62%);

                background-size: cover;
                background-repeat: no-repeat;
            }
        }

        .org-settings-list {
            display: none;
        }

        .normal-settings-list,
        .org-settings-list {
            position: relative;
        }

        .settings-sticky-bar {
            position: sticky;
            z-index: 1;
            background-color: hsl(0deg 0% 100%);
            top: 0;
        }
    }

    .settings-header {
        padding-top: 1px;

        &.mobile {
            display: none;
            border-bottom: 1px solid hsl(0deg 0% 87%);

            .fa-chevron-left {
                float: left;
                position: relative;
                top: 14px;
                left: 10px;
            }
        }

        & h1 {
            text-align: center;
            font-size: 1.1em;
            line-height: 1;
            margin: 15px;
            text-transform: uppercase;
        }

        .exit {
            font-weight: 600;
            position: absolute;
            top: 10px;
            right: 10px;
            color: hsl(0deg 0% 67%);
            cursor: pointer;
        }

        .exit-sign {
            float: right;
            position: relative;
            top: 1px;
            margin-left: 3px;
            font-size: 1.5rem;
            line-height: 1;
            font-weight: 600;
            cursor: pointer;
        }
    }

    .content-wrapper {
        position: absolute;
        left: $settings_sidebar_width;
        width: calc(100% - $settings_sidebar_width);
        height: 100%;
        overflow: hidden;

        .settings-header {
            width: 100%;
            height: $settings_header_height;
            box-sizing: border-box;
            border-bottom: 1px solid hsl(0deg 0% 87%);

            & h1 .section {
                font-weight: 400;
                color: inherit;
                opacity: 0.6;
            }
        }

        #settings_content {
            position: relative;
            width: 100%;
            height: calc(100% - $settings_header_height);

            float: left;
            overflow: auto;

            background-color: hsl(0deg 0% 0% / 2%);
        }
    }

    .display-settings-form select {
        width: 245px;
    }
}

#profile-settings,
#edit-user-form {
    .custom_user_field {
        padding-bottom: 20px;

        .field_hint {
            color: hsl(0deg 0% 67%);
        }

        & textarea {
            width: max(206px, 25vw);
            max-width: 320px;
            height: 80px;
        }

        &:hover .remove_date {
            display: inline-flex;
        }

        .remove_date {
            opacity: 0.5;
            display: none;
            cursor: pointer;
            position: relative;
            top: 2px;
            left: -20px;

            &:hover {
                opacity: 1;
            }
        }

        .datepicker {
            cursor: default;
        }

        .person_picker {
            min-width: 206px;
        }
    }

    #show_my_user_profile_modal {
        width: 100%;
        top: 20px;
        position: sticky;
    }

    #show_my_user_profile_modal i {
        padding-left: 2px;
        vertical-align: middle;
    }

    & input,
    input[type="url"] {
        /* Override undesired Bootstrap default. */
        margin-bottom: 0;
    }
}

.dropdown-list-widget {
    & button.dropdown-toggle {
        text-align: left;

        .fa-chevron-down {
            float: right;
            position: relative;
            top: 2px;
            padding-left: 5px;
            color: hsl(0deg 0% 58%);
            font-weight: lighter;
        }

        &.dropdown-toggle {
            /* Match settings for select elements. */
            padding: 4px 6px;

            & span {
                line-height: 20px;
                height: 1.4em;
            }
        }

        &:disabled i {
            display: none;
        }
    }

    & button.multiselect_btn {
        /* Matches the dropdown input margin so as to keep it aligned */
        margin-left: 9px;
        margin-top: 4px;
    }

    & a.dropdown_list_reset_button {
        /* Prevent dark theme from overriding background. */
        background: unset !important;
        border: none;
        margin-left: 10px;

        &:disabled {
            display: none;
        }
    }

    .dropdown-search > input[type="text"] {
        margin: 9px;
        /* 100% - 2* (9px (margin) + 1px (border) + 6px (padding)) */
        width: calc(100% - 32px);
    }

    .dropdown-menu {
        top: -7px; /* -(margin+padding), both are set by bootstrap. */
        bottom: auto;
    }

    .dropdown-list-wrapper {
        position: relative;
        height: auto;
        max-height: 200px;
        overflow-y: auto;
        margin-top: 0;
        display: block;
    }

    .dropdown-list-body {
        position: relative;
        margin-top: 0;
        display: block;

        /* In bootstrap v2.3.2, we strictly need
        .dropdown-menu > li > a as the order of the elements
        for the bootstrap style to be applied.
        Since we use a combination of dropdown + simplebar here,
        the structure cannot be possible since simplebar inserts
        elements of its own, so we copy over that style
        from bootstrap to here. */
        & li a {
            display: block;
            padding: 3px 20px;
            clear: both;
            font-weight: normal;
            line-height: 20px;
            color: hsl(0deg 0% 20%);
            white-space: nowrap;

            &:hover {
                color: hsl(0deg 0% 100%);
                text-decoration: none;
                background-color: hsl(200deg 100% 38%);
                background-image: linear-gradient(
                    to bottom,
                    hsl(200deg 100% 40%),
                    hsl(200deg 100% 35%)
                );
            }
        }
    }
}

.subsection-failed-status p {
    background-color: hsl(0deg 43% 91%);
    padding: 2px 6px;
    border-radius: 4px;
    margin: 0 0 0 5px;
}

#muted_topics_table {
    width: 90%;
    margin: 0 auto;

    & tbody {
        border-bottom: none;
    }
}

#admin-user-list .last_active {
    width: 100px;
}

.required-text {
    &:empty::after {
        content: attr(data-empty);
        display: block;

        font-style: italic;
        color: hsl(0deg 0% 67%);
    }

    &.thick:empty::after {
        width: 100%;
    }
}

#payload_url_inputbox,
#service_name_list {
    & input[type="text"] {
        width: 340px;
    }
}

.dropdown-title {
    margin-bottom: 3px;
}

@supports (-moz-appearance: none) {
    #settings_page select {
        appearance: none;
        background: hsl(0deg 0% 100%) url("../images/dropdown.png") right / 20px
            no-repeat;
        padding-right: 20px;
    }
}

.profile-field-choices {
    display: inline-block;

    & hr {
        margin-top: 0;
        margin-bottom: 5px;
    }

    .choice-row {
        margin-top: 8px;

        & input {
            width: 190px;
        }

        & button {
            margin-left: 2px;
        }
    }

    > .choice-row:first-of-type {
        margin-top: 0;
    }
}

.custom_user_field,
.bot_owner_user_field {
    .pill-container {
        padding: 2px 6px;
        min-height: 24px;
        max-width: 206px;
        background-color: hsl(0deg 0% 100%);

        &:focus-within {
            border-color: hsl(206deg 80% 62% / 80%);
            outline: 0;
            outline: 1px dotted \9;

            box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%),
                0 0 8px hsl(206deg 80% 62% / 60%);
        }
    }
}

#get_api_key_button {
    display: block;
}

#attachment-stats-holder {
    position: relative;
    margin-top: 13px;
    display: inline-block;
}

.hide-org-settings {
    display: none;
}

.collapse-settings-btn {
    margin: 10px 0 0 10px;
    color: hsl(200deg 100% 40%);

    &:hover {
        cursor: pointer;
        color: hsl(208deg 56% 38%);
    }
}

#toggle_collapse {
    margin-left: 2px;
    display: inline-block;
}

.admin_exports_table {
    margin-bottom: 20px;
}

.settings_textarea {
    color: hsl(0deg 0% 33%);
    background-color: hsl(0deg 0% 100%);
    border-radius: 4px;
    vertical-align: middle;
    border: 1px solid hsl(0deg 0% 80%);
    padding: 4px 6px;

    box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%);
    transition: border linear 0.2s, box-shadow linear 0.2s;

    &:focus {
        border-color: hsl(206.5deg 80% 62% / 80%);
        outline: 0;

        box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%),
            0 0 8px hsl(206.5deg 80% 62% / 60%);
    }

    &:disabled {
        cursor: not-allowed;
        background-color: hsl(0deg 0% 93%);
    }
}

@media (width < $lg_min) {
    .upload-size {
        display: none;
    }

    .user-avatar-section,
    .realm-icon-section {
        display: block;
    }

    #settings_content .warning {
        display: none;
    }

    .subsection-failed-status p {
        margin: 5px 0 0;
    }
}

/* This value needs to match with the same in subscriptions.css, as
   we have some shared styles declared there */
@media (width < $md_min) {
    .profile-settings-form {
        .user-avatar-section {
            flex: 100%;
        }
    }

    #settings_overlay_container {
        /* this variable allows JavaScript to detect this media query */
        --single-column: yes;
    }

    #settings_page {
        .settings-header.mobile {
            display: block;

            &:not(.slide-left) .section {
                /* When viewing the settings list we hide the active section. */
                display: none;
            }
        }

        .content-wrapper {
            .settings-header {
                display: none;
            }

            #settings_content {
                height: 100%;
            }

            &.right {
                top: 47px;
            }
        }

        .sidebar-wrapper {
            width: 100%;
        }

        .sidebar {
            position: absolute;
            width: 100%;
            border: none;
            /* 48px is the height of settings header and 45px is the height of tab-container */
            height: calc(100% - 93px);

            & li.active {
                /* Don't highlight the active section in the settings list. */
                background: inherit;
                border-bottom: 1px solid hsl(0deg 0% 93%);
            }
        }
    }
}

@media (width < $sm_min) {
    .user_row,
    .settings-section {
        .bot_type,
        .last_active {
            display: none;
        }
    }

    #pw_strength {
        margin: auto;
    }

    #linkifier-settings .new-linkifier-form input,
    #playground-settings .new-playground-form input,
    #profile-field-settings .new-profile-field-form input {
        width: calc(100% - 20px) !important;
    }

    #linkifier-settings .new-linkifier-form label,
    #playground-settings .new-playground-form label,
    #profile-field-settings .new-profile-field-form label {
        display: block;
        width: 120px;
        padding: 0;
        padding-top: 0;
        text-align: center;
        margin: auto;
        float: none;
    }

    #change_password_modal,
    #change_email_modal {
        width: 400px;
    }
}

@media (width < $ml_min) {
    #api_key_buttons,
    #download_zuliprc {
        flex-direction: column;
        margin-top: 5px;
    }

    #settings_page,
    #edit-user-form {
        .custom_user_field textarea {
            width: calc(100% - 25px);
        }
    }

    .topic_date_muted {
        display: none;
    }

    #change_password_modal,
    #change_email_modal {
        width: 300px;
    }
}

@media (width < $mm_min) {
    .deactivate_realm_button {
        margin-top: 20px;
    }
}

@media only screen and (width < $lg_min) {
    /* Show bot-information-box at full width on small
       screen sizes. Not having this media query breaks the
       information box */
    .bots_list .bot-information-box {
        width: calc(100% - 10px);
        max-height: unset;
    }
}

#edit-linkifier-form {
    #edit-linkifier-pattern,
    #edit-linkifier-url-format-string {
        width: 400px;
    }

    & label {
        margin-bottom: 4px;
    }

    #edit-linkifier-pattern-status,
    #edit-linkifier-format-status {
        margin-top: 10px;
    }

    & input {
        margin-bottom: 0;
    }
}

.settings_panel_list_header {
    position: relative;

    & h3 {
        display: inline-block;
    }

    & input.search {
        float: right;
        font-size: 1em;
        max-width: 160px;
        margin-top: 12px;
    }
}

#add-new-custom-profile-field-form,
#edit-custom-profile-field-form-modal {
    .disabled_label {
        cursor: default;
        opacity: 0.7;
    }
}

~~~
#### navbar.css ####
~~~
.nav-zulip-logo {
    background-image: url("data:image/svg+xml,%3Csvg width='108' height='28' viewBox='0 0 108 28' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cg clip-path='url(%23clip0_555_12341234)'%3E%3Cpath d='M25.0534 4.18667C25.0534 5.59714 24.4217 6.85034 23.4589 7.6106L14.1128 15.9802C13.9392 16.1294 13.7136 15.8888 13.8388 15.688L17.267 8.80536C17.3631 8.61266 17.2385 8.37582 17.0414 8.37582H3.7444C1.68498 8.37582 0 6.49104 0 4.18791C0 1.88416 1.68498 6.14715e-07 3.7444 6.14715e-07H21.309C23.3684 -0.00124264 25.0534 1.88353 25.0534 4.18667ZM3.7444 28H21.309C23.3684 28 25.0534 26.1152 25.0534 23.8121C25.0534 21.5083 23.3684 19.6242 21.309 19.6242H8.01203C7.81489 19.6242 7.69029 19.3873 7.78638 19.1946L11.2146 12.312C11.3398 12.1112 11.1142 11.8706 10.9406 12.0198L1.59447 20.3882C0.631713 21.1478 0 22.4016 0 23.8121C0 26.1152 1.68498 28 3.7444 28ZM36.136 20.2825L43.8715 9.11804V9.02107H36.8588V5.97633H48.6431V8.10292L41.0762 19.1225V19.2195H48.764V22.2642H36.136V20.2825V20.2825ZM57.1505 5.97633V15.353C57.1505 18.1559 58.2106 19.5819 60.0909 19.5819C62.0189 19.5819 63.0789 18.2286 63.0789 15.353V5.97633H66.7421V15.1105C66.7421 20.137 64.2116 22.5291 59.97 22.5291C55.8728 22.5291 53.4631 20.2576 53.4631 15.0621V5.97633H57.1505V5.97633ZM72.3333 5.97633H76.0207V19.1704H82.4792V22.2636H72.3333V5.97633ZM90.7454 5.97633V22.2636H87.058V5.97633H90.7454ZM96.3359 6.1939C97.4686 6.00058 99.0593 5.85574 101.3 5.85574C103.566 5.85574 105.181 6.29088 106.265 7.16054C107.301 7.98233 108 9.33561 108 10.9301C108 12.5252 107.47 13.8785 106.506 14.7966C105.253 15.9808 103.397 16.5123 101.228 16.5123C100.747 16.5123 100.313 16.4881 99.9756 16.4396V22.2636H96.3366V6.1939H96.3359ZM99.975 13.5888C100.288 13.6615 100.674 13.6851 101.204 13.6851C103.156 13.6851 104.361 12.6943 104.361 11.0271C104.361 9.52894 103.324 8.63442 101.493 8.63442C100.746 8.63442 100.24 8.70715 99.975 8.77926V13.5888V13.5888Z' fill='white'%3E%3C/path%3E%3C/g%3E%3Cdefs%3E%3CclipPath id='clip0_555_12341234'%3E%3Crect width='108' height='28' fill='white'%3E%3C/rect%3E%3C/clipPath%3E%3C/defs%3E%3C/svg%3E");
    background-repeat: no-repeat;
    width: 108px;
}

.top-menu {
    position: fixed;
    width: 100%;
    background: hsl(240deg 100% 10% / 60%);
    backdrop-filter: blur(10px);
    color: hsl(0deg 0% 100%);
    z-index: 10;
    overflow: hidden;
}

.top-menu-container {
    /*   1280px + 32px for paddings on the edges */
    max-width: 1312px;
    margin: 0 auto;
    display: flex;
    align-items: center;
}

.top-menu-logo {
    overflow: hidden;
    opacity: 0.85;
    /* 14*2 = 28px = height of logo svg */
    padding: 14px;
    margin: 0 16px;
    flex-shrink: 0;
}

.top-menu-items-group-1,
.top-menu-items-group-2 {
    display: flex;
}

.top-menu-items-group-1 {
    margin-right: 32px;
}

.top-menu-item,
.top-menu-mobile a {
    &,
    &:hover,
    &:focus,
    &:visited {
        color: hsl(0deg 0% 100% / 80%);
    }
}

.top-menu-item {
    display: flex;
    align-items: center;
    flex-shrink: 0;
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 28px;
    padding: 14px;
    user-select: none;
    cursor: pointer;
    transition-property: background, color;
    transition-duration: 0.05s;
    transition-timing-function: ease-out;
    color: hsl(0deg 0% 100% / 80%);
}

.top-menu-item:hover {
    color: hsl(0deg 0% 100%);
    background: hsl(240deg 100% 10% / 10%);
    transition-duration: 0.05s;
}

.top-menu-item:active {
    color: hsl(0deg 0% 100%);
    background: hsl(240deg 100% 10% / 20%);
}

.top-menu-item.top-menu-tab,
.top-menu-item.top-menu-tab:hover,
.top-menu-item.top-menu-tab:active {
    opacity: 1;
    background: none;
}

.top-menu-item-spacer {
    flex-shrink: 1;
    flex-grow: 1;
}

.top-menu-item input[type="radio"],
.top-menu-tab-input-unselect {
    display: none;
}

.top-menu-item.top-menu-tab {
    padding: 0;
    position: relative;
    cursor: auto;
}

.top-menu-tab-unselect {
    position: absolute;
    inset: 0;
    z-index: 0;
    cursor: pointer;
}

.top-menu-tab-input:checked + label {
    transition: background, color 0.2s;
    background: hsl(240deg 100% 10% / 60%);
    color: hsl(0deg 0% 100%);
    pointer-events: none;
    user-select: none;
}

.top-menu-tab label {
    padding: 16px;
    cursor: pointer;
    transition-property: background, color;
    transition-duration: 0.1s;
    transition-timing-function: ease-out;
    z-index: 5;
    color: hsl(0deg 0% 100% / 80%);

    /* Override bootstrap */
    margin-bottom: 0;
    font-size: inherit;
    line-height: inherit;
}

.top-menu-tab label::after {
    pointer-events: none;
    content: " ";
    display: inline-block;
    vertical-align: middle;
    width: 16px;
    height: 16px;
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24' fill='none' stroke='rgba(255%2c255%2c255%2c0.8)' stroke-width='3' stroke-linecap='round' stroke-linejoin='round' class='feather feather-chevron-down'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e");
    background-size: 16px;
    margin-left: 2px;
    margin-right: -8px;
    background-repeat: no-repeat;
}

.top-menu-tab .top-menu-tab-input:checked + label::after {
    transform: rotate(-180deg);
}

.top-menu-tab .top-menu-tab-input:not(:checked) + label:hover {
    background: hsl(240deg 100% 10% / 10%);
    color: hsl(0deg 0% 100%);
    transition-duration: 0.1s;
}

.top-menu-tab .top-menu-tab-input:not(:checked) + label:active {
    background: hsl(240deg 100% 10% / 20%);
    color: hsl(0deg 0% 100%);
}

.top-menu-tab label.top-menu-tab-user-label::after {
    display: block;
    position: absolute;
    right: 16px;
    top: 50%;
    transform: translateY(-45%);
}

.top-menu-tab
    .top-menu-tab-input:checked
    + label.top-menu-tab-user-label::after {
    transform: translateY(-45%) rotate(-180deg);
}

.top-menu-submenu-backdrop {
    background: hsl(240deg 100% 10%);
    opacity: 0;
    height: 0;
    width: 100%;
    transition: all 0.05s;
}

.top-menu-tab-input-unselect:not(:checked) + .top-menu-submenu-backdrop {
    height: 334px;
    opacity: 1;
}

.top-menu-tab-label-unselect {
    position: absolute;
    display: none;
    /* To account for scrollbar if any present. */
    right: 15px;
    top: 60px;
    width: 44px;
    height: 44px;
    background-size: 32px;
    background-repeat: no-repeat;
    /* Close menu icon */
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24' fill='none' stroke='rgba(255,255,255,1)' stroke-width='1.5' stroke-linecap='round' stroke-linejoin='round'%3e%3cline x1='18' y1='6' x2='6' y2='18'%3e%3c/line%3e%3cline x1='6' y1='6' x2='18' y2='18'%3e%3c/line%3e%3c/svg%3e");
    background-position: center;
    cursor: pointer;
    opacity: 0.5;
}

.top-menu-tab-label-unselect:hover {
    opacity: 0.8;
}

.top-menu-tab-label-unselect:active {
    opacity: 1;
}

.top-menu-tab-input-unselect:not(:checked) ~ .top-menu-tab-label-unselect {
    display: block;
}

.top-menu-submenu {
    position: absolute;
    top: 60px;
    display: flex;
    gap: 16px;
    opacity: 0;
    visibility: hidden;
    transition: all 0.2s;
}

.top-menu-tab .top-menu-tab-user-label {
    max-width: 140px;
    padding-right: 28px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.top-menu-tab-user-img {
    width: 24px;
    height: 24px;
    display: inline;
    vertical-align: middle;
    border-radius: 3px;
    margin-right: 4px;
}

.top-menu-mobile-user-img {
    width: 28px;
    height: 28px;
    display: inline;
    vertical-align: text-top;
    border-radius: 3px;
    margin-right: 4px;
}

@media (max-width: 1400px) {
    .top-menu-submenu.singup-column {
        justify-content: flex-end;
        right: 55px;
    }
}

@media (max-width: 1170px) {
    .top-menu-tab .top-menu-tab-user-label {
        max-width: 84px;
    }
}

@media (max-width: 1024px) {
    .top-menu-tab .top-menu-tab-user-label {
        max-width: 40px;
    }

    .top-menu-tab .top-menu-tab-user-label span {
        display: none;
    }
}

.top-menu-tab-input:checked ~ .top-menu-submenu {
    opacity: 1;
    visibility: visible;
}

.top-menu-submenu-column {
    display: flex;
    flex-direction: column;
    padding-top: 16px;
    flex-shrink: 0;
    max-width: 420px;

    .top-menu-submenu-list {
        margin: 0;
        list-style: none;

        .top-menu-submenu-list-item {
            font-size: 17px;
            font-weight: 400;
            color: hsl(0deg 0% 100% / 90%);
            border-radius: 2px;
            cursor: pointer;

            &:hover {
                background: hsl(0deg 0% 100% / 10%);
            }

            &:active {
                background: hsl(0deg 0% 100% / 20%);
            }

            & a {
                display: block;
                padding: 6px 16px;
                text-decoration: none;
                line-height: 125%;
                color: hsl(0deg 0% 100% / 90%);
            }
        }
    }
}

.top-menu-mobile .top-menu-mobile-item a {
    padding: 10px 10px 10px 53px;
    border-radius: 2px;
    cursor: pointer;
    text-decoration: none;
    display: block;

    &:hover {
        background: hsl(0deg 0% 100% / 10%);
    }

    &:active {
        background: hsl(0deg 0% 100% / 20%);
    }
}

.top-menu-submenu-section {
    padding-left: 16px;
    font-size: 17px;
    opacity: 0.6;
    margin-bottom: 4px;
    letter-spacing: 2px;
}

.top-menu-mobile {
    display: none;
    background: hsl(240deg 100% 10% / 40%);
    backdrop-filter: blur(10px);
    z-index: 20;

    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 60px;

    overflow: auto;
    font-style: normal;
    font-weight: 500;
    font-size: 20px;
    line-height: 28px;
    letter-spacing: 0.02em;
    font-feature-settings: "pnum" on, "lnum" on;
    color: hsl(0deg 0% 100% / 80%);

    transition: all 0.2;
    overscroll-behavior: contain;
}

.top-menu-mobile[open] {
    bottom: 0;
    height: 100%;
    background: hsl(240deg 100% 5.9% / 80%);
    backdrop-filter: blur(20px);
}

.top-menu-mobile-items-group-1,
.top-menu-mobile-items-group-2 {
    display: flex;
    flex-direction: column;
    margin-bottom: 24px;
}

.top-menu-mobile-items-group-1 summary,
.top-menu-mobile-items-group-1 a,
.top-menu-mobile-items-group-2 summary,
.top-menu-mobile-items-group-2 a {
    cursor: pointer;
    transition: background 0.4s ease-out;
}

.top-menu-mobile-items-group-1 summary,
.top-menu-mobile-items-group-2 summary {
    padding: 10px 10px 10px 23px;
    user-select: none;
}

.top-menu-mobile-items-group-1 a,
.top-menu-mobile-items-group-2 a {
    padding-left: 53px;
}

@media (hover: hover) and (pointer: fine) {
    .top-menu-mobile-items-group-1 summary:hover,
    .top-menu-mobile-items-group-2 summary:hover {
        background: hsl(0deg 0% 100% / 10%);
        transition: none;
    }
}

.top-menu-mobile-items-group-1 summary:active,
.top-menu-mobile-items-group-2 summary:active {
    background: hsl(0deg 0% 100% / 10%);
}

.top-menu-mobile-item-summary::marker {
    content: "";
}

.top-menu-mobile-item-summary::before {
    content: "";
    display: inline-block;
    vertical-align: middle;
    margin-top: -4px;
    margin-right: 4px;
    width: 24px;
    height: 24px;
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24' fill='none' stroke='rgba(255%2c255%2c255%2c0.7)' stroke-width='2' stroke-linecap='round' stroke-linejoin='round' class='feather feather-chevron-down'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e");
    transition: transform 0.12s ease-out;
    transform: rotate(-90deg);
}

.top-menu-mobile details[open] > summary::before {
    transform: rotate(0deg);
}

.top-menu-mobile-submenu {
    display: flex;
    flex-direction: column;
    font-size: 18px;
    margin-bottom: 18px;

    .top-menu-submenu-list {
        margin: 0;
        list-style: none;

        .top-menu-submenu-list-item {
            font-size: 17px;
            font-weight: 400;
            line-height: 26px;
            color: hsl(0deg 0% 100% / 90%);
            border-radius: 2px;
            cursor: pointer;

            &:hover {
                background: hsl(0deg 0% 100% / 10%);
            }

            &:active {
                background: hsl(0deg 0% 100% / 20%);
            }

            & a {
                text-decoration: none;
                padding: 5px 0 5px 53px;
                display: block;
            }
        }
    }
}

.top-menu-mobile-submenu-section {
    letter-spacing: 0.1em;
    color: hsl(0deg 0% 100% / 40%);
    opacity: 0.8;
    text-transform: uppercase;
    margin-top: 8px;
    font-size: 17px;
    padding-left: 53px;
    user-select: none;
    pointer-events: none;
}

.top-menu-mobile-summary {
    cursor: pointer;
    position: sticky;
    top: 0;
    z-index: 1;
    transition: all 0.3s;
    height: 60px;
    overflow: hidden;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.top-menu-mobile-summary:active {
    background: hsl(229deg 47% 17% / 80%);
    backdrop-filter: blur(10px);
}

.top-menu-mobile[open] > .top-menu-mobile-summary {
    background: hsl(229deg 47% 17% / 80%);
    backdrop-filter: blur(10px);
}

/* For browsers which don't support blur */
@supports not (
    (backdrop-filter: blur(10px)) or (-webkit-backdrop-filter: blur(10px))
) {
    .top-menu {
        background: hsl(240deg 100% 10% / 80%);
    }

    .top-menu-mobile {
        background: hsl(240deg 100% 10% / 80%);
    }

    .top-menu-mobile[open] {
        background: hsl(240deg 100% 5.9% / 100%);
    }

    .top-menu-mobile-summary:active {
        background: hsl(229deg 47% 17% / 95%);
    }

    .top-menu-mobile[open] > .top-menu-mobile-summary {
        background: hsl(229deg 47% 17% / 95%);
    }
}

.top-menu-mobile[open] > .top-menu-mobile-summary:active {
    background: hsl(229deg 47% 20% / 100%);
}

.top-menu-mobile-summary::marker {
    content: "";
    display: none;
}

.top-menu-mobile-summary::after {
    display: block;
    height: 32px;
    float: right;
    content: "MENU";
    line-height: 32px;
    color: hsl(0deg 0% 100% / 80%);
    padding-right: 38px;
    font-size: 20px;
    font-weight: 400;
    letter-spacing: 2px;
    margin-right: 16px;
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24' fill='none' stroke='rgba(255,255,255,0.9)' stroke-width='1.5' stroke-linecap='round' stroke-linejoin='round'%3e%3cline x1='3' y1='12' x2='21' y2='12'%3e%3c/line%3e%3cline x1='3' y1='6' x2='21' y2='6'%3e%3c/line%3e%3cline x1='3' y1='18' x2='21' y2='18'%3e%3c/line%3e%3c/svg%3e");
    background-repeat: no-repeat;
    background-size: 32px;
    background-position: right;
    transition: background, letter-spacing 0.2s;
}

.top-menu-mobile-summary:active::after {
    letter-spacing: 2px;
}

.top-menu-mobile[open] > summary::after {
    content: "Close";
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24' fill='none' stroke='rgba(255,255,255,0.9)' stroke-width='1.5' stroke-linecap='round' stroke-linejoin='round'%3e%3cline x1='18' y1='6' x2='6' y2='18'%3e%3c/line%3e%3cline x1='6' y1='6' x2='18' y2='18'%3e%3c/line%3e%3c/svg%3e");
}

@media (hover: hover) and (pointer: fine) {
    .top-menu-mobile-summary:hover {
        background: hsl(229deg 47% 18% / 100%);
    }

    .top-menu-mobile[open] > .top-menu-mobile-summary:hover {
        background: hsl(229deg 47% 18% / 100%);
    }

    .top-menu-mobile-summary:hover::after {
        letter-spacing: 4px;
    }
}

/* menu responsivity */
@media (max-width: 1311px) {
    .top-menu {
        background: hsl(240deg 100% 10% / 50%);
    }

    .top-menu-logo {
        margin-right: 0;
    }

    .top-menu-item {
        padding: 16px 12px;
        font-size: 18px;
        font-weight: 500;
    }
}

@media (max-width: 940px) {
    .top-menu {
        display: none;
    }

    .top-menu-logo {
        margin-right: unset;
        display: inline-block;
    }

    .top-menu-mobile {
        display: block;
    }
}

~~~
#### subscriptions.css ####
~~~
#subs_page_loading_indicator {
    margin: 10px auto;
}

.member_list_loading_indicator,
.subscriber_list_loading_indicator {
    margin: 10px auto;
}

.member_list_loading_indicator:empty,
.subscriber_list_loading_indicator:empty {
    margin: 0;
}

.subscriptions div #response {
    overflow-wrap: break-word;
}

.subscription_settings .btn {
    border-radius: 2px;
}

.stream-email {
    font-family: "Source Code Pro", monospace;
    padding: 10px;
    font-size: 0.85rem;
    background-color: hsl(0deg 0% 98%);
    border: 1px solid hsl(0deg 0% 87%);
    border-radius: 4px;
}

.sp-preview {
    width: 20px;
    border: none;
    box-shadow: 0 0 1px hsl(0deg 0% 0%);
}

.sp-replacer {
    margin-right: 12px;
    border: none;
    box-shadow: 0 0 2px hsl(0deg 0% 0% / 80%);
}

.stream-email .email-address {
    display: block;
    margin: auto;
    word-wrap: break-word;
    word-break: break-all;
    white-space: normal;
}

.muted-sub,
.control-label-disabled {
    color: hsl(0deg 0% 64%);
}

.sub_setting_checkbox .muted-sub label,
.sub_setting_checkbox .control-label-disabled label {
    cursor: not-allowed;
}

.mute-note {
    font-size: 90%;
    opacity: 0.5;
}

.hide-mute-note {
    display: none;
}

.sub_setting_control {
    display: inline-block;
    margin-right: 10px;
}

.create_user_group_plus_button,
.create_stream_plus_button {
    font-size: 24px;
    font-weight: 500;
    position: relative;
    top: 2px;
    border: 1px solid hsl(0deg 0% 80%);
    border-radius: 5px;
    background-color: hsl(0deg 0% 100%);
    color: hsl(0deg 0% 0%);
    margin: 0 0 0 5px;
    height: 27px;

    &:hover {
        border: 1px solid hsl(0deg 0% 47%);
    }

    & span {
        position: relative;
        top: -5px;
    }
}

.create_user_group_button {
    position: relative;
    top: 7px;
    margin: 0 7px 0 0;
}

#create_user_group_description,
#create_stream_description {
    width: calc(100% - 15px);
}

.user_group_creation_error,
.stream_creation_error {
    display: none;
    margin-left: 2px;
    color: hsl(0deg 100% 50%);
}

/* TODO: Unify with settings.css definition */
h3.stream_setting_subsection_title,
h3.user_group_setting_subsection_title {
    display: inline-block;
    font-size: 1.5em;
    font-weight: normal;
    line-height: 1.5;
}

h4.stream_setting_subsection_title,
h4.user_group_setting_subsection_title {
    display: inline-block;
    font-size: 1.35em;
    font-weight: normal;
    line-height: 1.5;
}

.member-list-box,
.subscriber-list-box {
    text-align: center;
    border-left: 1px solid hsl(0deg 0% 87%);
    border-right: 1px solid hsl(0deg 0% 87%);
    border-radius: 4px;

    .member_list_container,
    .subscriber_list_container {
        position: relative;
        /* 2*45px (settings header) + 38px(tab-container row) + 20px (margin for .inner-box) + 134px (add user input and search widget area) = 282px */
        max-height: calc(95vh - 282px);
        overflow: auto;
        text-align: left;
        -webkit-overflow-scrolling: touch;

        .member-list,
        .subscriber-list {
            width: 100%;
            margin: auto;
            border-radius: 6px;

            & tbody {
                border-bottom: none;

                & tr:last-of-type {
                    border-bottom: none;
                }
            }

            & tr {
                border-bottom: 1px solid hsl(0deg 0% 93%);

                & td,
                th {
                    padding: 4px 0 4px 5px;
                    vertical-align: middle;

                    &:first-of-type {
                        padding-left: 10px;
                    }
                }
            }

            .subscriber_list_remove {
                display: inline-block;
            }

            & tbody:empty::after,
            &:empty::after {
                content: "No subscribers to this stream.";
                display: block;

                color: hsl(0deg 0% 67%);
                padding: 5px 5px 5px 10px;
            }

            & thead th {
                &:first-of-type {
                    border-top-left-radius: 4px;
                }

                &:last-of-type {
                    border-top-right-radius: 4px;
                }

                position: sticky;
                top: 0;
                z-index: 1;
            }

            .hidden-subscriber-email {
                font-style: italic;
            }
        }
    }
}

.subscriber-name,
.subscriber-email {
    padding: 5px;
}

.subscriber-email {
    margin-left: 20px;
    padding-right: 8px;
}

.subscriber_list_add,
.member_list_add {
    width: 100%;
    margin: 0 0 10px;

    .user_group_subscription_request_result,
    .stream_subscription_request_result {
        & a {
            color: inherit;
        }
    }
}

.member-search,
.subscriber-search {
    margin: 10px 0 0;

    .search {
        max-width: 160px;
    }
}

.subscriber_list_add .form-inline,
.member_list_add .form-inline {
    margin-bottom: 0;
}

.add_subscribers_container {
    display: inline-flex;
    width: 100%;
    align-items: center;

    .add_subscriber_btn_wrapper {
        padding-left: 5px;
    }
}

.remove-subscriber-form {
    margin: 0;
}

#subscriptions h1 {
    font-size: 25px;
    font-weight: 300;
    padding-top: 40px;
}

.subscriptions-container .subscriptions-header .fa-chevron-left,
.user-groups-container .user-groups-header .fa-chevron-left,
#settings_overlay_container .settings-header.mobile .fa-chevron-left {
    position: relative;
    transform: translate(-50px, 0);
    opacity: 0;
    color: hsl(0deg 0% 67%);

    float: left;
    padding: 2px 10px;

    cursor: pointer;

    transition: all 0.3s ease;
}

.user-groups-container .user-groups-header.slide-left .fa-chevron-left,
.subscriptions-container .subscriptions-header.slide-left .fa-chevron-left,
#settings_overlay_container
    .settings-header.mobile.slide-left
    .fa-chevron-left {
    transform: translate(0, 0);
    opacity: 1;
}

.user-groups-container,
.subscriptions-container {
    position: relative;
    height: 95%;
    border-radius: 4px;
    padding: 0;
    width: 97%;
    overflow: hidden;
    max-width: 1200px;
    max-height: 1000px;

    .search-container .tab-switcher .ind-tab {
        width: auto;
    }

    .user-groups-header,
    .subscriptions-header {
        padding: 12px;
        text-align: center;
        text-transform: uppercase;
        font-weight: 700;
        border-bottom: 1px solid hsl(0deg 0% 87%);

        .fa-chevron-left {
            display: none;
        }

        .user-groups-title,
        .subscriptions-title {
            display: inline-block;
            transition: all 0.3s ease;
            transform: translate(-13px, 0);
        }

        .exit {
            font-weight: 600;
            position: absolute;
            top: 10px;
            right: 10px;
            color: hsl(0deg 0% 67%);
            cursor: pointer;
        }
    }

    .exit-sign {
        position: relative;
        top: 1px;
        margin-left: 3px;
        font-size: 1.5rem;
        line-height: 1;
        font-weight: 600;
        cursor: pointer;
    }

    .left,
    .right {
        position: relative;
        display: inline-block;
        vertical-align: top;
        width: 50%;
        height: calc(100% - 45px);
        margin: 0 -2px;
    }

    .left {
        border-right: 1px solid hsl(0deg 0% 87%);

        .search-container {
            padding: 6px 8px;
            border-bottom: 1px solid hsl(0deg 0% 87%);
            display: flex;
            justify-content: space-between;
        }
    }

    .right {
        width: calc(50% + 1px);

        .nothing-selected {
            display: block;
            margin-top: calc(45vh - 75px);
            text-align: center;
            font-size: 1em;
            margin-left: 2em;
            margin-right: 2em;

            & span {
                color: hsl(0deg 0% 67%);
            }

            & button {
                padding: 6px 10px 8px;
                display: block;
                margin: 0 auto 10px;
            }
        }

        .display-type {
            padding: 2px;
            text-align: center;
            font-weight: 600;
            border-bottom: 1px solid hsl(0deg 0% 87%);

            &.preview::after {
                content: "Preview";
            }

            &.preferences::after {
                content: "Preferences";
            }

            .stream-info-title,
            .user-group-info-title {
                display: none;
                font-size: 1.5em;
                line-height: 1;
                margin: 9px 0;
                font-weight: 600;

                .large-icon {
                    display: inline-block;
                }

                .fa-lock {
                    position: relative;
                }

                .zulip-icon-globe {
                    font-size: 15px;
                }
            }
        }
    }

    & input[type="text"].small {
        border: 1px solid hsl(0deg 0% 80%);
        border-radius: 4px;
        padding: 3px;
        outline: none;
        color: hsl(0deg 0% 27%);
        text-align: center;

        &:focus {
            text-align: left;
        }

        &:valid {
            text-align: left;
        }
    }
}

#search_stream_name,
#search_group_name {
    width: 100%;
    padding: 3px 5px;
    margin: 8px 0;
    margin-left: 10px;
    margin-right: -15px !important;
    display: inline-block;
    border-radius: 5px;
    box-shadow: none;
    padding-right: 20px;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
}

.stream_name_search_section,
.group_name_search_section {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-bottom: 0;
    height: auto;
    border-bottom: 1px solid hsl(0deg 0% 87%);
}

.user-groups-list,
.streams-list {
    position: relative;
    overflow: auto;
    -webkit-overflow-scrolling: touch;
    height: calc(100% - 85px);
    width: 100%;
}

.user-groups-list {
    /*
        This height rule is temporary for this preparatory commit and
        will be removed as we add other components widgets in groups list
        and its styling similar to streams list.
    */
    height: calc(100% - 42px) !important;
}

#clear_search_stream_name,
#clear_search_group_name {
    right: 5px !important;
}

.stream-title {
    font-size: 1.3em;
    font-weight: 400;
}

.user-group-creation-body,
.stream-creation-body {
    & section.block {
        margin-bottom: 20px;
    }

    #announce-new-stream {
        margin: 25px auto;

        & div[class^="fa"] {
            margin-left: 3px;
            margin-right: 8px;
        }
    }
}

.stream-row,
.group-row {
    padding: 15px 10px 11px;
    border-bottom: 1px solid hsl(0deg 0% 93%);
    cursor: pointer;

    .check {
        width: 25px;
        height: 25px;
        position: relative;
        margin-right: 8px;
        margin-top: 9px;
        background-size: 60% auto;
        background-repeat: no-repeat;
        background-position: center center;

        & svg {
            fill: transparent;
            width: 70%;
            margin: 0% 15%;
        }

        &.checked:hover svg {
            opacity: 0.5;
        }

        &.disabled {
            pointer-events: none;
            visibility: hidden;
        }

        .sub_unsub_status {
            display: inline-block !important;
            height: auto !important;
            width: auto !important;

            .loading_indicator_spinner {
                width: 100%;
                height: 100%;
                margin: 0;
            }

            .loading_indicator_spinner svg path {
                fill: hsl(178deg 100% 40%);
            }
        }
    }

    .checked svg {
        fill: hsl(170deg 48% 54%);
    }

    .icon {
        width: 35px;
        height: 35px;
        margin-right: 8px;
        margin-top: 4px;
        background-color: hsl(300deg 100% 25%);
        border-radius: 4px;
        color: hsl(0deg 0% 100%);

        .symbol {
            font-weight: 600;
            font-size: 1.1em;
        }

        .fa-lock {
            font-size: 1.4em;
        }

        .hashtag {
            font-size: 1.4em;
            font-weight: 600;
        }
    }

    .sub-info-box,
    .group-info-box {
        width: calc(100% - 90px);

        .top-bar,
        .bottom-bar {
            display: flex;
            justify-content: space-between;
            position: relative;
        }

        .top-bar .stream-name,
        .top-bar .group-name-wrapper,
        .bottom-bar .description {
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            margin-right: 12px;
        }

        .top-bar .subscriber-count,
        .bottom-bar .stream-message-count {
            white-space: nowrap;
            color: hsl(0deg 0% 67%);
        }

        .top-bar .subscriber-count-text,
        .top-bar .subscriber-count-lock,
        .bottom-bar .stream-message-count-text {
            margin-right: 5px;
        }

        .top-bar > div {
            display: inline-block;
            vertical-align: top;
        }

        .top-bar .stream-name,
        .top-bar .group-name-wrapper {
            font-weight: 600;
        }

        .bottom-bar {
            margin-top: 2px;
            line-height: 1.5;
        }

        .bottom-bar > div {
            display: inline-block;
            vertical-align: bottom;
        }
    }

    &.active {
        background-color: hsl(0deg 0% 93%);
    }

    > div {
        display: inline-block;
        vertical-align: top;
    }

    &:hover .check:not(.checked) svg,
    &.active:hover .check:not(.checked) svg {
        fill: hsl(0deg 0% 87%);
    }

    .check:not(.checked):hover svg,
    &.active .check:not(.checked):hover svg {
        fill: hsl(0deg 0% 72%);
    }

    &::selection,
    .icon .hashtag::selection {
        background-color: transparent;
    }
}

.stream-row .sub-info-box .description:empty::after,
.group-row .group-info-box .description:empty::after {
    content: attr(data-no-description);
    font-style: italic;
    color: hsl(0deg 0% 67%);
}

#groups_overlay,
#subscription_overlay {
    #user-group-creation,
    #stream-creation {
        overflow: auto;
        outline: none;
        -webkit-overflow-scrolling: touch;

        .user-group-creation-body,
        .stream-creation-body {
            /*
                45px (.subscriptions-header) +  44px (.display-type) + 60px (.modal-footer) + 15px (padding for .simplebar-content)
            */
            height: calc(95vh - 164px);
            padding: 15px 15px 0;
        }

        .modal-footer {
            position: absolute;
            bottom: 0;
            width: calc(100% - 27px);
            padding-top: 9px;
        }

        .add_all_users_to_user_group,
        .add_all_users_to_stream {
            margin-left: 10px;
        }

        .create_user_group_member_list_header,
        .create_stream_subscriber_list_header {
            margin-top: 10px;
            margin-bottom: 3px;

            & h5 {
                display: inline-block;
            }
        }

        .add-user-list-filter {
            width: 140px;
            float: right;
        }

        #user_group_creation_form,
        #stream_creation_form {
            margin: 0;

            .user_group_create_info.show {
                margin: 5px;
            }

            #user_group_creating_indicator,
            #stream_creating_indicator {
                &:not(:empty) {
                    position: absolute;
                    width: 100% !important;
                    height: calc(100% - 105px) !important;
                    display: flex !important;
                    justify-content: center;
                    align-items: center;
                    background-color: hsl(0deg 0% 100% / 90%);
                    z-index: 1;
                }

                .loading_indicator_text {
                    font-weight: 400;
                }
            }
        }
    }

    .inner-box {
        margin: 20px;
    }

    .group_settings_header,
    .stream_settings_header {
        white-space: nowrap;
        display: flex;
        margin-left: 15px;

        .tab-container {
            .ind-tab {
                padding: 3px 4px;
                width: 80px;
            }
        }

        .button-group {
            padding-top: 5px;
            margin-left: auto;
            margin-right: 15px;

            .subscribe-button,
            #preview-stream-button,
            .deactivate {
                margin-right: 3px;
                text-decoration: none;
            }
        }
    }

    .group-header,
    .stream-header {
        white-space: nowrap;
        padding-top: 10px;
        display: flex;
        align-items: center;

        .group-name-wrapper,
        .stream-name {
            display: inline-block;
            position: relative;
            font-size: 1.5em;
            font-weight: 600;
            margin-left: -3px;
            margin-top: -5px;
            white-space: nowrap;

            .group-name,
            .sub-stream-name {
                display: block;
                max-width: 100%;
                overflow: hidden;
                text-overflow: ellipsis;
            }
        }

        .button-group {
            margin-left: 1rem;

            .deactivate {
                margin-right: 3px;
                text-decoration: none;
            }
        }

        .subscribe-button.unsubscribed {
            color: hsl(156deg 39% 54%);
            border-color: hsl(156deg 39% 77%);

            &:active {
                background-color: hsl(156deg 39% 54% / 20%);
            }
        }

        .large-icon {
            display: inline-block;
            vertical-align: top;
            margin-right: 5px;
            margin-top: -5px;
            font-size: 1.5em;

            &.hash::after {
                top: -1px;
                font-size: 1.09em;
                font-weight: 800;
            }

            .zulip-icon-globe {
                font-size: 15px;
            }
        }

        .group_change_property_info,
        .stream_change_property_info {
            vertical-align: top;
            margin: -5px 0 0;
        }
    }

    .group-description-wrapper,
    .stream-description {
        word-break: break-all;
        margin-bottom: 5px;

        .no-description {
            font-style: italic;
            color: hsl(0deg 0% 67%);
        }
    }

    .checkmark {
        display: none;
        margin-left: 5px;
        color: hsl(0deg 0% 67%);

        cursor: pointer;

        &.show {
            display: block;
        }
    }

    .hash::after {
        position: relative;
        content: "#";
    }

    .settings {
        position: relative;
        height: calc(100% - 45px);
        overflow-y: auto;
        -webkit-overflow-scrolling: touch;

        .tab-container {
            padding-top: 5px;
        }
    }

    .subscription_settings {
        display: none;
        position: relative;
        width: 100%;
        margin: 0 auto;
        border-radius: 4px;
        top: -1px;

        &.show {
            display: block;
        }
    }

    #personal-stream-settings {
        .stream_change_property_status {
            margin: 9px auto 3px 3px;
        }
    }

    .copy_email_button {
        padding: 10px 15px;
    }

    .loading_indicator_text {
        font-weight: 400;
        line-height: 20px;
    }

    .subsection-parent .input-group {
        & input[type="checkbox"] {
            margin-top: 0;
        }

        &:last-of-type {
            border-bottom: none;
        }

        .sp-replacer {
            box-shadow: none;
        }

        & input[type="radio"] {
            margin-right: 5px;
        }

        .inline {
            display: inline !important;
        }
    }
}

div.settings-radio-input-parent {
    border-bottom: 1px solid hsl(0deg 0% 87%);
    margin: 2px 0 2px 5px;
    padding: 2px 0;

    &:last-of-type {
        border-bottom: none;
    }

    & label.radio {
        display: inline;
        margin: 5px;
    }

    & input {
        float: left;
        width: auto;
        cursor: pointer;
        margin: 3.5px 0 1px;

        &:focus {
            outline: 1px dotted hsl(0deg 0% 20%);
            outline: 5px auto -webkit-focus-ring-color;
            outline-offset: -2px;
        }

        &:disabled {
            cursor: not-allowed;
        }
    }
}

.stream-permissions,
.stream-creation-body {
    .input-group {
        margin-bottom: 10px;

        &.message-retention-setting-group {
            & input {
                width: 5ch;
                text-align: right;
            }
        }
    }

    .settings_select {
        /* Match with select elements in settings page */
        min-width: 325px;
        max-width: 100%;
        height: fit-content;
    }

    & select.stream_post_policy_setting {
        margin-bottom: 10px;
    }

    .dropdown-list-widget {
        .dropdown-toggle {
            margin-bottom: 10px;
            min-width: 325px;
            max-width: 100%;
        }
    }
}

#change_user_group_description,
#change_stream_description {
    width: 100%;
    height: 80px;
    margin-bottom: 4px;
    box-sizing: border-box;
}

.stream-permissions .stream-message-retention-days-input input[type="text"] {
    border-radius: 5px;
    box-shadow: none;
    margin: 0;
    height: inherit;
}

@media (width < $lg_min) {
    .user-groups-container,
    .subscriptions-container {
        max-width: 95%;
    }

    #groups_overlay,
    #subscription_overlay {
        .left {
            width: 40%;
        }

        .right {
            width: calc(60% - 1px);
        }
    }
}

@media (width < $lg_min) {
    .subscriptions-container .left .search-container {
        flex-wrap: wrap;
    }

    .search-container {
        text-align: center;
    }

    #groups_overlay .group_settings_header,
    #subscription_overlay .stream_settings_header {
        flex-wrap: wrap;
    }
}

/* Note that this block has settings_page CSS as well, and thus needs
   to match the media queries in settings.css.

   Longer-term we should extract this logic two-column-overlay class
   to read more naturally. */
@media (width < $md_min) {
    .user-groups-container,
    .subscriptions-container {
        position: relative;
        overflow: hidden;

        .search-container {
            text-align: left;
        }

        .user-groups-header .fa-chevron-left,
        .subscriptions-header .fa-chevron-left {
            display: block;
        }
    }

    #groups_overlay .left,
    #groups_overlay .right,
    #subscription_overlay .left,
    #subscription_overlay .right,
    #settings_page .content-wrapper.right {
        position: absolute;
        display: block;
        margin: 0;
        width: 100%;
        height: calc(100% - 45px);

        border: none;
    }

    #groups_overlay .right,
    #subscription_overlay .right,
    #settings_page .content-wrapper.right {
        position: absolute;
        left: 101%;

        top: 45px;
        background-color: hsl(0deg 0% 98%);
        border-top: none;

        transition: all 0.3s ease;
        z-index: 10;

        &.show {
            left: 0%;
        }
    }

    #groups_overlay {
        .display-type {
            display: none;
        }
    }

    #subscription_overlay,
    #groups_overlay {
        .user-groups-container,
        .subscriptions-container {
            height: 95%;
        }

        .settings {
            overflow: auto;
            -webkit-overflow-scrolling: touch;
        }
    }
}

@media (width < $sm_min) {
    #groups_overlay .user_group_settings_wrapper,
    #subscription_overlay .subscription_settings {
        .button-group {
            display: block;
            float: right;
            margin-top: 10px;
        }

        .group-header,
        .stream-header {
            .button-group {
                margin-top: -5px;
            }
        }

        .group_change_property_info,
        .stream_change_property_info {
            /* For small widths where there is not enough space
            to show alert beside stream name we set its display
            to block so it is shown in new line. But to avoid
            it covering whole screen width we set max-width
            so that it does not losses inline-block appearance. */

            /* TODO: This will probably be not required once
            we have tabbed navigation as button group width
            will be smaller. */
            display: block;
            max-width: max-content;
            white-space: nowrap;
        }

        .save-button-controls {
            display: block;
            margin: 0 0 10px;

            &.hide {
                display: none;
            }
        }
    }
}

@media (width <= 500px) {
    #groups_overlay,
    #subscription_overlay {
        .groups_settings_header,
        .stream_settings_header {
            display: block;
            text-align: center;
            margin-left: 0;

            .tab-container {
                .ind-tab {
                    width: 85px;
                }
            }
        }
    }
}

~~~
#### landing_page.css ####
~~~
html {
    width: 100vw;
    overflow-x: hidden;
}

body {
    margin: 0;
    background-color: hsl(0deg 0% 100%) !important;
    color: hsl(0deg 0% 27%);
    line-height: normal;

    max-width: 100vw;
}

/* -- generic styles -- */

h1,
h2,
h3 {
    margin: 10px 0;

    font-weight: 300;
    line-height: 1.2;
}

h1 {
    font-size: 2em;
}

h2 {
    font-size: 1.8em;
}

p {
    margin: 10px 0;
    font-weight: normal;
    line-height: 1.5;
}

ul {
    font-weight: normal;
}

a {
    position: relative;
    cursor: pointer;
    color: hsl(170deg 47% 33%);

    &:hover,
    &:visited {
        color: hsl(170deg 47% 33%);
    }

    &:hover,
    &:focus {
        text-decoration: none;
    }

    &.arrow {
        &::after {
            content: " ";
            display: inline-block;
            position: relative;
            height: 17px;
            width: 17px;
            top: 3px;
            background-image: url("../../images/landing-page/arrow.png");
            background-size: 100%;
            margin-left: 5px;
        }
    }

    &.silver {
        text-decoration: underline;
    }
}

span a:hover,
p a:hover,
ul a:hover,
ol a:hover {
    text-decoration: underline;
}

.flex {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.float {
    &.left {
        float: left;
    }

    &.right {
        float: right;
    }

    &.clear {
        clear: both;
    }
}

.small {
    font-size: 0.8em;
}

.box-shadow {
    box-shadow: 0 0 80px hsl(0deg 0% 0% / 12%);
}

.grey {
    color: hsl(0deg 0% 60%);
}

.dark-grey {
    color: hsl(0deg 0% 40%);
}

.bold {
    font-weight: 600;
}

.padded-content {
    padding: 50px;
}

.clear-float {
    clear: both;
}

*::selection {
    background-color: hsl(31deg 84% 60% / 30%);
}

.center {
    text-align: center;
}

/* -- component styling -- */
.button,
button {
    padding: 5px 12px;

    font-family: inherit;
    font-size: 0.7em;
    background-color: hsl(0deg 0% 100%);
    color: hsl(0deg 0% 27%);

    line-height: 20px;
    border-radius: 4px;
    border: 1px solid hsl(0deg 0% 80%);
    outline: none;

    &:active {
        background-color: hsl(0deg 0% 98%);
        border-color: hsl(0deg 0% 73%);
    }

    &.green {
        color: hsl(0deg 0% 100%);
        background-color: hsl(170deg 47% 53%);
        border-color: hsl(169deg 45% 43%);

        &:hover {
            background-color: hsl(170deg 47% 58%);
        }

        &:active {
            background-color: hsl(170deg 47% 48%);
        }
    }

    &.black-current-value {
        color: hsl(0deg 0% 20%);
        background-color: transparent;
        border-color: hsl(0deg 0% 53%);
    }
}

.silver {
    color: hsl(0deg 0% 100%) !important;
    opacity: 0.8;

    &:hover {
        opacity: 1;
    }

    &.bold {
        font-weight: 600;
    }
}

/* -- main panel styling -- */
.main {
    width: calc(100% - 200px - 20px);
    margin: 0 auto;
}

/* -- modify portico.css -- */
.app-main {
    max-width: none;
    min-width: 0;
    padding: 0 !important;
}

.header {
    display: none;
}

/* -- features page css -- */
.portico-landing {
    position: relative;

    padding-top: 120px;

    z-index: 1;

    &.show {
        opacity: 1;
    }
}

.portico-landing.features-app {
    position: relative;
    overflow-x: hidden;
    padding-top: 0;

    z-index: 2;

    .gradients {
        z-index: -1;
    }

    & section {
        max-width: 1440px;
        display: flex;
        flex: 1 1 auto;
        flex-flow: row wrap;
        justify-content: space-around;
        margin: 40px auto;
        padding: 0 30px;
        color: hsl(219deg 21% 21%);

        &.hero {
            display: flex;
            align-items: center;
            justify-content: center;

            height: 400px;
            padding: 100px 100px 50px;

            margin: 0;

            max-width: none;

            color: hsl(0deg 0% 100%);

            background-color: hsl(0deg 0% 0% / 10%);

            .copy {
                max-width: 800px;
                margin: 0 auto;

                text-align: center;
            }

            & h1 {
                margin: 0;
                font-size: 3.7em;
            }

            & h2 {
                font-size: 1.8em;
                margin: 30px auto 0;

                max-width: 600px;
                line-height: 1.3;
            }

            .image {
                height: 400px;
                width: 40%;
                background-color: hsl(0deg 0% 0% / 5%);
            }
        }

        &.keyboard-shortcuts {
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            max-width: none;
            padding: 50px;
            /* this should only be a thing if the section above is not white */
            margin-top: 0;
            background-color: hsl(219deg 21% 21%);
            color: hsl(219deg 76% 93%);

            & img {
                &.overflow-wave {
                    width: 685px;
                    right: 0;
                    top: -168px;
                    position: absolute;
                }

                &.image {
                    width: 600px;
                    margin-left: 100px;
                }
            }

            & h3 {
                font-size: 3em;
            }

            .feature-block {
                width: 50%;
            }

            & p {
                font-size: 1.2em;
            }

            & a.cta {
                font-size: 1em;
                color: hsl(170deg 52% 70%);
            }
        }

        &.messages {
            display: flex;
            justify-content: center;
            align-items: center;

            margin: 50px auto;
            padding: 0 50px;

            .image {
                width: calc(100% - 500px - 100px);
                margin: 50px 0 50px 50px;
                max-width: 500px;
            }

            .features {
                max-width: 500px;

                & h2 {
                    margin: 0;
                }

                .feature-block {
                    display: block;
                    margin: 30px 0;
                }
            }
        }

        &.notifications {
            position: relative;

            padding: 50px 100px;
            max-width: calc(1000px);

            background-color: hsl(0deg 0% 100%);
            border-radius: 10px;

            box-shadow: 10px 20px 80px hsl(0deg 0% 0% / 15%);
            margin: 100px auto 150px;
            text-align: center;

            .envelope {
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                max-height: 40vw;
            }

            & h2 {
                position: relative;

                margin-bottom: 120px;
                top: 0;
            }

            .feature-list {
                position: relative;

                display: inline-block;
                vertical-align: top;
                text-align: left;

                margin: 35px 0 0 20px;

                z-index: 1;

                & h3 {
                    position: relative;

                    margin: 15px 0 15px 50px;

                    font-size: 1.2em;
                    font-weight: 400;

                    color: hsl(0deg 0% 53%);

                    &::before {
                        content: " ";
                        display: block;
                        position: absolute;

                        left: -35px;
                        top: 0;
                        width: 20px;
                        height: 20px;

                        border-radius: 4px;

                        background-image: url("../../images/checkbox-green.svg");
                        background-size: 100% auto;
                        background-position: center;
                        background-repeat: no-repeat;
                    }
                }
            }

            .image-block {
                width: 400px;
                height: 280px;

                background: linear-gradient(
                    135deg,
                    hsl(0deg 0% 0% / 5%),
                    hsl(0deg 0% 0% / 20%)
                );
                border-radius: 4px;

                background-image: url("../../images/landing-page/features/notifications.jpg");
                background-size: contain;
                background-position: center;
                background-repeat: no-repeat;

                display: inline-block;
            }
        }

        .feature-block {
            display: inline-block;
            vertical-align: top;
        }

        & h2 {
            font-size: 2.5em;
            text-align: center;
            margin: 0 10px;
            line-height: 1.6;
            flex: 1 0 100%;
        }

        > .feature-block {
            padding: 10px 20px;
            flex: 1 1 320px;
            color: inherit;
        }

        & a {
            &.feature-block {
                &:hover {
                    box-shadow: 0 3px 10px hsl(0deg 0% 75%);
                }

                &:active {
                    box-shadow: 0 3px 10px hsl(0deg 0% 50%);
                }
            }
        }
    }

    .cta {
        &::after {
            content: "\2192";

            margin-left: 5px;
            transform: scaleX(2);

            transition: all 0.3s ease;
        }

        &:hover {
            &::after {
                margin-left: 10px;
            }
        }
    }

    .feature-block {
        & h3 {
            font-size: 1.2em;
            font-weight: 600;
        }

        & p {
            margin: 0;

            opacity: 0.8;
        }
    }
}

/* -- hello page -- */
.portico-landing.hello {
    background-color: transparent;
    color: hsl(219deg 23% 33%);

    .hero-buttons {
        margin-top: 40px;
    }
}

.portico-landing.hello .hero {
    position: relative;
    padding: 60px 50px 30px;

    color: hsl(0deg 0% 100%);

    overflow: hidden;

    .content {
        position: relative;
        z-index: 1;

        text-align: center;

        & p {
            font-weight: 400;
            opacity: 0.85;
        }
    }

    & header {
        width: 850px;
        display: inline-block;
        text-align: left;

        & h1 {
            font-size: 3em;
            font-weight: 400;

            text-shadow: 0 0 20px hsl(0deg 0% 100% / 20%);
        }

        & p {
            margin: 30px 0;

            font-size: 1.5em;
            font-weight: 300;
            line-height: 1.4;
            text-shadow: 0 0 5px hsl(164deg 74% 15% / 30%),
                0 0 20px hsl(0deg 0% 100% / 20%);
        }

        & a {
            display: block;
            margin: 20px auto 0;
            text-align: center;
        }

        & button {
            margin-top: 0;
            padding: 12px 20px;

            background-color: hsl(0deg 0% 100%);
            border: 2px solid hsl(0deg 0% 100%);

            font-size: 1.2em;
            font-weight: 500;
            color: hsl(148deg 23% 51%);

            box-shadow: 0 3px 10px hsl(0deg 0% 0% / 20%);

            transition: all 0.2s ease;

            &:hover {
                box-shadow: 0 3px 10px hsl(0deg 0% 100% / 20%);
            }

            &:active {
                box-shadow: 0 3px 20px hsl(0deg 0% 100% / 50%);
            }
        }
    }
}

.portico-landing.hello .gradients .gradient {
    position: absolute;
    left: 0;
    width: 100%;
    height: 1100px;

    &.dark-blue {
        background: linear-gradient(
            10deg,
            hsl(196deg 58% 14% / 0%) 50%,
            hsl(196deg 58% 14% / 70%)
        );
    }

    &.green {
        background: linear-gradient(
            -25deg,
            hsl(156deg 47% 47% / 0%) 40%,
            hsl(156deg 47% 47%)
        );
    }

    &.blue {
        background: linear-gradient(
            25deg,
            hsl(196deg 38% 51% / 0%) 40%,
            hsl(196deg 38% 51%)
        );
    }

    &.sunburst {
        background: linear-gradient(
            5deg,
            hsl(49deg 71% 68% / 0%) 20%,
            hsl(49deg 71% 68%)
        );
    }

    &.white-fade {
        background: linear-gradient(
            0deg,
            hsl(0deg 0% 98%) 0%,
            hsl(0deg 0% 98% / 0%) 40%
        );
    }
}

@keyframes waves {
    0% {
        transform: rotate(0);
    }

    50% {
        transform: rotate(180deg);
    }

    100% {
        transform: rotate(360deg);
    }
}

@keyframes wavesBackward {
    0% {
        transform: rotate(0);
    }

    50% {
        transform: rotate(-180deg);
    }

    100% {
        transform: rotate(-360deg);
    }
}

/* -- compare css -- */
.compare,
.compare-education {
    background: linear-gradient(
        198deg,
        hsl(170deg 34% 47%),
        hsl(146deg 31% 60%)
    );
    color: hsl(0deg 0% 100%);

    .table-container {
        overflow-x: auto;
    }

    .gradients .gradient.white-fade {
        background: none;
    }

    .text-header .text-content h1 {
        margin-top: 0;
    }

    .padded-content {
        max-width: 900px;
        margin: 0 auto;
        position: relative; /* To place the content on top of gradients. */
        z-index: 2;
    }

    & table {
        min-width: 550px;
        padding: 33px;
        border: 20px solid transparent;
        width: 100%;
        text-align: left;
        border-collapse: collapse;
        font-weight: 400;
        color: hsl(0deg 0% 100% / 80%);

        & thead th {
            &:last-of-type {
                width: 120px;
            }

            &.uniform {
                width: 20%;
            }
        }

        & td:not(:first-of-type),
        th:not(:first-of-type) {
            text-align: center;
        }
    }

    & thead {
        border-bottom: 3px solid hsl(0deg 0% 0% / 10%);

        & th {
            font-weight: 600;
            padding: 15px 0;
            font-size: 18px;

            color: hsl(0deg 0% 100%);

            &.normal {
                font-weight: normal;
                color: inherit;
            }

            &:nth-of-type(1) {
                width: 28%;
                background-color: hsl(222deg 24% 31%);
            }

            &:nth-of-type(2) {
                width: 18%;
                background-color: hsl(187deg 94% 20%);
            }

            &:nth-of-type(3),
            &:nth-of-type(4),
            &:nth-of-type(5),
            &:nth-of-type(6) {
                width: 18%;
                background-color: hsl(162deg 67% 25%);
            }
        }
    }

    .gradients {
        position: static;
    }

    & tbody tr {
        border-bottom: 1px solid hsl(360deg 0% 100% / 3%);

        & td {
            padding: 10px 0;

            &:nth-of-type(1) {
                background-color: hsl(222deg 20% 40%);
            }

            &:nth-of-type(2) {
                background-color: hsl(186.9deg 90.3% 28.4%);
            }

            &:nth-of-type(3),
            &:nth-of-type(4),
            &:nth-of-type(5),
            &:nth-of-type(6) {
                background-color: hsl(162deg 44% 38%);
            }

            &.no {
                text-align: center;
            }

            &.yes::before {
                content: " ";
                display: inline-block;

                width: 27px;
                height: 27px;
                background-image: url("../../images/landing-page/checkmark.png");
                background-size: 100% auto;
            }

            &.no::before {
                content: "\d7";

                position: relative;
                display: inline-block;

                top: 3px;

                font-size: 2.5rem;
                font-weight: 500;
                line-height: 0.9;

                opacity: 0.4;
            }

            & a {
                font-size: 0.9rem;
                font-weight: 400;
                text-transform: uppercase;
            }
        }
    }

    & p {
        font-weight: 300;
    }

    .terms {
        margin-top: 30px;
        font-weight: 400;
        font-size: 0.7em;

        line-height: 1.2;

        color: hsl(0deg 24% 23%);

        & a {
            color: hsl(170deg 47% 73%);
        }
    }
}

.compare-education {
    color: hsl(0deg 0% 0%);
    background: none;

    & table {
        min-width: 650px;

        .number {
            font-weight: 800;

            &.one {
                color: hsl(0deg 0% 100% / 40%);
            }
        }

        & td:first-of-type {
            padding: 10px 10px 10px 0;
        }
    }
}

/* -- faq css -- */
.faqs {
    position: relative;
    background-color: hsl(0deg 0% 98%);

    .padded-content {
        position: relative;
        z-index: 1;
    }

    & header {
        max-width: 700px;
        margin: 0 auto;

        & h1 span {
            vertical-align: top;
        }
    }

    .faq {
        margin: 50px auto;
        max-width: 700px;
        font-size: 1.2em;
        color: hsl(223deg 6% 25%);

        .question {
            font-weight: 600;
            color: hsl(222deg 20% 40%);
            font-size: 1.1em;
        }

        .answer {
            margin: 20px 0 0;
            font-weight: 400;
        }
    }

    /* the last faq in the box shouldn't have an extra 50px of margin. */
    .faq-box div:last-of-type {
        margin-bottom: 10px;
    }

    .faq-header-link {
        color: hsl(0deg 0% 0%);

        &:hover {
            text-decoration: underline;
        }
    }
}

.screen {
    .line {
        width: 100%;
        height: 6px;
        margin: 8px 0;

        background-color: hsl(0deg 0% 93%);
        border-radius: 3px;

        &.small {
            width: 60%;
        }

        &.micro {
            display: inline-block;
            vertical-align: top;

            width: 15%;
        }

        &.nano {
            display: inline-block;
            vertical-align: top;

            width: 10%;
        }

        &.med {
            width: 80%;
        }

        &.red {
            background-color: hsl(350deg 42% 77%);
        }

        &.blue {
            background-color: hsl(193deg 42% 77%);
        }

        &.green {
            background-color: hsl(119deg 42% 77%);
        }

        &.orange {
            background-color: hsl(30deg 42% 77%);
        }
    }

    .top {
        .avatar {
            display: inline-block;
            vertical-align: top;

            width: 20px;
            height: 20px;
            background-color: hsl(0deg 0% 73%);
            border-radius: 4px;
        }

        .top-line {
            display: inline-block;
            vertical-align: top;

            width: 50px;
            margin-top: 0;

            background-color: hsl(0deg 0% 73%);
        }
    }

    .navbar {
        background-color: hsl(170deg 48% 54%);
        padding: 10px;
    }

    .center-page {
        height: 100%;
        position: relative;

        overflow: hidden;

        .message-feed {
            height: calc(100% - 20px);
            margin-top: 20px;

            transition: all 0.1s ease;
        }
    }

    .message-feed {
        .message .content {
            margin-left: 24px;
            position: relative;
            top: -15px;
        }

        .stream {
            padding: 3px 5px 0;
            margin: 0 5px;

            background-color: hsl(0deg 0% 100%);
            border-radius: 4px;

            box-shadow: 0 0 15px hsl(0deg 0% 0% / 1%);
        }
    }
}

.portico-landing.hello .screen {
    position: relative;
    margin: -300px auto 0;

    width: 600px;
    height: 350px;

    padding: 10px 30px;

    border-radius: 12px;
    box-shadow: 0 0 50px hsl(0deg 0% 0% / 20%);

    background-color: hsl(0deg 0% 27%);

    z-index: 1;

    &::before {
        content: " ";
        position: absolute;
        top: calc(50% - 5px);
        left: 20px;

        width: 10px;
        height: 10px;

        border-radius: 5px;
        background-color: hsl(0deg 0% 13%);
    }

    &::after {
        content: " ";
        position: absolute;
        top: calc(50% - 12.5px);
        right: 8px;

        width: 25px;
        height: 25px;

        border-radius: 13px;
        background-color: hsl(0deg 0% 73%);
    }

    .main-page {
        display: inline-block;

        height: calc(100% - 30px);
        width: calc(100% - 30px);
        margin: 10px;

        border: 5px solid hsl(0deg 0% 13%);
        border-radius: 4px;

        background-color: hsl(0deg 0% 98%);
    }
}

.portico-landing.hello .features {
    padding: 50px 0 100px;

    background-color: hsl(0deg 0% 100%);
}

.portico-landing.hello .open-source {
    text-align: center;

    position: relative;
    z-index: 1;

    background-color: hsl(217deg 22% 93%);

    .flex {
        min-height: 0;
        padding: 50px 0;
    }

    & img {
        margin: 0 2%;
        width: 28%;
        max-width: 500px;
        display: inline-block;
    }

    .il-block {
        display: inline-block;
        vertical-align: top;
        width: 50%;
        max-width: 700px;
        text-align: left;
    }

    & h2 {
        font-weight: normal;
    }
}

.carousel.carousel-fade .carousel-inner {
    .item {
        display: block;
        opacity: 0;
        height: 0;
        transition: opacity 0.4s ease;
        visibility: hidden;

        &.active {
            opacity: 1;
            height: auto;
            visibility: visible;

            &.left,
            &.right {
                left: 0;
                opacity: 0;
                z-index: 2;
            }
        }

        &.next.left,
        &.prev.right {
            opacity: 1;
            z-index: 1;
        }
    }

    .item-inner {
        position: relative;
    }

    .next.left .item-inner,
    .prev.right .item-inner {
        padding: 30px 20px;
    }
}

.portico-landing .tour {
    color: hsl(0deg 0% 0%);
    width: 1200px;
    max-width: 100%;
    margin: 0 auto;
}

.tour .carousel-inner .item-container {
    width: 80%;
    height: 520px;
    margin: 20px auto;
    padding: 30px 20px;
    background: linear-gradient(
        hsl(220deg 20% 97% / 40%),
        hsl(220deg 20% 97% / 90%)
    );
    border-radius: 12px;
    box-shadow: 0 3px 10px hsl(0deg 0% 0% / 2%);
    position: relative;
}

.tour .carousel-inner .start-button {
    padding: 11px 25px;
    font-size: 1.2rem;
    font-weight: 400;
    color: hsl(0deg 0% 100%);
    background: linear-gradient(
        145deg,
        hsl(191deg 56% 55%),
        hsl(169deg 65% 42%)
    );
    box-shadow: 0 3px 10px hsl(0deg 0% 0% / 20%);
    border: 0;
    position: absolute;
    left: 50%;
    margin-left: -100px;
    top: 50%;
    margin-top: -25px;
    width: 200px;
    height: 50px;
    z-index: 10;

    &:hover {
        background-color: hsl(169deg 65% 42%);
        box-shadow: 0 3px 10px hsl(0deg 0% 0% / 30%);
    }
}

.tour .carousel-inner .start-image {
    position: relative;
    margin: 0 auto;
    display: block;
    width: 100%;
    max-width: 100%;
    border: 1px solid hsl(0deg 0% 87%);
    opacity: 0.4;
}

.tour .carousel-inner .tour-item-header {
    margin: 0 0 30px 54px;
    max-width: 700px;
    font-size: 1.3em;
    text-align: left;
}

.tour .carousel-inner .tour-item-header-top-push {
    margin-top: 40px;
}

.tour .carousel-inner .tour-item-header-centered {
    text-align: center;
    margin-left: auto;
    margin-right: auto;
}

.tour .carousel-inner .zulip-slack-comparison {
    display: flex;
    text-align: left;
    width: 850px;
    max-width: 100%;
    margin: 20px auto 0;
    position: relative;

    .comparison-zulip {
        width: 500px;
    }

    .comparison-slack {
        width: 300px;
    }

    & img {
        max-width: 100%;

        &.zulip-streams-selected {
            width: 320px;
            border: 0;
        }

        &.slack-streams-selected {
            width: 200px;
        }

        &.zulip-unreads-arrows {
            width: 406px;
            border: 0;
        }

        &.slack-stream-unreads {
            width: 200px;
        }
    }

    .caption {
        text-align: left;
        font-weight: bold;
        margin-bottom: 10px;
    }
}

.tour .carousel-inner img {
    border: 1px solid hsl(210deg 8% 95%);

    &.centered-image {
        display: block;
        margin: 0 auto;
    }

    &.zulip-streams {
        width: 200px;
    }

    &.slack-streams {
        width: 200px;
    }

    &.zulip-topic {
        margin: -10px 0 0 50px;
        width: 800px;
    }

    &.slack-overwhelming {
        border: none;
        width: 750px;
        margin: -30px 0 0 50px;
    }

    &.zulip-easy {
        border: none;
        width: 700px;
        margin-left: 50px;
    }
}

.tour .carousel-inner .mobile-hide,
.tour .carousel-inner img.mobile-hide,
.tour .carousel-inner img.centered-image.mobile-hide {
    display: block;
}

.tour .carousel-inner .mobile-show,
.tour .carousel-inner img.mobile-show,
.tour .carousel-inner img.centered-image.mobile-show {
    display: none;
}

.tour .carousel-inner .comparison-slack img {
    margin: 0;
}

.tour .carousel-inner .other-resources {
    text-align: left;
    margin: 30px auto;
    max-width: 600px;

    .other-resources-section {
        display: inline-block;
        width: 48%;
        text-align: center;
        vertical-align: top;

        & img {
            border: 0;
            display: block;
            margin: 0 auto;
        }
    }
}

.tour .carousel-inner .call-to-action {
    display: inline-block;
    margin: 40px auto;
    padding: 11px 25px;

    font-size: 1.2rem;
    line-height: 20px;
    font-weight: 400;
    color: hsl(0deg 0% 100%);

    background: linear-gradient(
        145deg,
        hsl(191deg 56% 55%),
        hsl(169deg 65% 42%)
    );
    box-shadow: 0 3px 10px hsl(0deg 0% 0% / 20%);
    border-radius: 4px;

    &:hover {
        background-color: hsl(169deg 65% 42%);
        box-shadow: 0 3px 10px hsl(0deg 0% 0% / 30%);
    }
}

.tour .carousel-control {
    background: 0;
    border: 0;
    color: hsl(223deg 13% 52%);
    font-size: 2em;
    top: 50%;
    font-weight: 400;
    opacity: 1;
    border-radius: 0;

    &:hover {
        color: hsl(220deg 23% 33%);
    }

    &.right {
        right: 40px;
    }

    &.left {
        left: 40px;
    }
}

.carousel-indicators {
    margin: 20px 0 0;
    display: flex;
    justify-content: center;
    padding-left: 0;
    list-style: none;
    position: relative;
    top: auto;
    right: auto;

    & li {
        position: relative;
        flex: 0 1 auto;
        width: 10px;
        height: 10px;
        border-radius: 10px;
        margin-right: 10px;
        margin-left: 10px;
        text-indent: -999px;
        cursor: pointer;
        background-color: hsl(222deg 12% 66%);
        transition: background 0.1s ease;

        &::before {
            position: absolute;
            top: -10px;
            left: 0;
            display: inline-block;
            width: 100%;
            height: 10px;
            content: "";
        }

        &::after {
            position: absolute;
            bottom: -10px;
            left: 0;
            display: inline-block;
            width: 100%;
            height: 10px;
            content: "";
        }

        &.active {
            background-color: hsl(220deg 23% 33%);
        }
    }
}

.portico-landing .testimonials {
    color: hsl(0deg 0% 100%);
    background-color: hsl(168deg 43% 24%);
}

.portico-landing .testimonials .text-header .text-content {
    float: left;
}

.portico-landing .testimonials .quote-container {
    width: 98%;
    margin: 30px auto 20px;
    padding-left: 2%;

    font-size: 1.2rem;
}

.portico-landing .testimonials .carousel {
    min-height: 250px;
}

.portico-landing .testimonials .carousel-quotes {
    width: 60%;
    margin: auto;
}

.portico-landing .testimonials .carousel-inner {
    width: 100%;
    left: -2%;
}

.portico-landing .testimonials .fa-chevron-left,
.portico-landing .testimonials .fa-chevron-right {
    color: hsl(0deg 0% 100%);
    opacity: 0.5;
    position: absolute;
    font-size: 36px;
    top: 40%;
}

.portico-landing .testimonials .fa-chevron-right {
    right: 10%;
}

.portico-landing .testimonials .fa-chevron-left {
    left: 10%;
}

.portico-landing .testimonials .fa-chevron-left:hover,
.portico-landing .testimonials .fa-chevron-right:hover {
    opacity: 1;
}

.portico-landing .testimonials blockquote::before {
    content: "“";
    margin-left: -10px;
    margin-right: -3px;
}

.portico-landing .testimonials blockquote::after {
    content: "”";
}

.portico-landing .testimonials blockquote + cite {
    display: block;
    margin-top: 5px;
    margin-bottom: 30px;

    color: hsl(0deg 0% 100%);
    opacity: 0.7;
    font-weight: 400;
    font-style: normal;
}

.portico-landing .testimonials blockquote {
    padding: 0;

    font-weight: 400;
    line-height: 1.6;
    text-align: left;
    border: none;

    opacity: 0.8;
}

.portico-landing .testimonials hr {
    width: 60%;
    margin: 0 auto;
    border: none;
    border-bottom: 1px solid hsl(0deg 0% 100% / 20%);
}

.portico-landing .testimonials .company-container {
    width: 60%;
    margin: 30px auto;
    text-align: left;
}

.portico-landing .testimonials .company-box {
    margin-top: 20px;
}

.portico-landing .testimonials .company-container header h2 {
    font-weight: 400;
    font-size: 1.5em;
}

.portico-landing .testimonials .company-container header .arrow {
    margin-top: 12px;
    font-weight: normal;
}

.portico-landing .testimonials .company-box .company {
    display: inline-block;
    margin: 10px 20px;

    height: 60px;
    width: calc(25% - 44px);

    background-color: hsl(0deg 0% 67%);
    background-size: contain;
    background-position: center;
    background-repeat: no-repeat;
}

/* -- company logos -- */
.portico-landing .testimonials .company-box .company.akamai {
    background-image: url("../../images/landing-page/logos/akamai.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.doctorondemand {
    background-image: url("../../images/landing-page/logos/doctorondemand.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.layershift {
    background-image: url("../../images/landing-page/logos/layershift.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.recurse {
    background-image: url("../../images/landing-page/logos/recurse.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.panjiva {
    background-image: url("../../images/landing-page/logos/panjiva.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.cmt {
    background-image: url("../../images/landing-page/logos/cambridge-mobile-telematics.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.levelup {
    background-image: url("../../images/landing-page/logos/levelup.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.mariadb {
    background-image: url("../../images/landing-page/logos/mariadb.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.wikimedia-outreach {
    background-image: url("../../images/landing-page/logos/wikimedia-outreach.png");
    background-color: transparent;
}

.portico-landing .testimonials .company-box .company.mixxx {
    background-image: url("../../images/landing-page/logos/mixxx.png");
    background-color: transparent;
    height: 45px;
}

.portico-landing.hello .apps {
    position: relative;
    padding: 200px 80px 100px;
    margin-top: -50px;

    background: linear-gradient(
        145deg,
        hsl(191deg 56% 55%),
        hsl(169deg 65% 42%)
    );

    color: hsl(0deg 0% 100%);
}

.portico-landing.hello .apps .triangle {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 150px 100vw 0 0;
    border-color: hsl(0deg 0% 98%) transparent transparent transparent;
}

.portico-landing.hello .apps .arrow {
    color: hsl(0deg 0% 100%);
    font-weight: 400;
}

.portico-landing.hello .apps .arrow::before {
    background-color: hsl(0deg 0% 100%);
}

.portico-landing.hello .apps .left-side,
.portico-landing.hello .apps .right-side {
    display: inline-block;
    vertical-align: top;
}

.portico-landing.hello .apps .left-side {
    width: calc(60% - 4px);
}

.portico-landing.hello .apps .right-side {
    width: calc(40% - 4px);
    text-align: center;
}

.portico-landing.hello .apps .left-side .content {
    width: 650px;
    margin: 50px auto;
}

.portico-landing.hello .apps .left-side .platform-icons {
    text-align: center;
}

.portico-landing.hello .apps .left-side .platform-icons .group h2 {
    font-size: 1.5em;
}

.portico-landing.hello .apps .left-side .platform-icons .group {
    display: inline-block;
    vertical-align: top;
    margin: 0 30px;

    text-align: center;
}

.portico-landing.hello .apps .left-side .platform-icons .group a {
    color: inherit;
}

.portico-landing.hello .apps .left-side .platform-icons .group i {
    display: inline-block;
    width: 80px;

    font-size: 3.5em;
    opacity: 0.8;
}

.portico-landing.hello .apps .left-side .platform-icons .group i:hover {
    opacity: 1;
}

.portico-landing.hello .apps .arrow::after {
    filter: brightness(4) saturate(0);
}

.portico-landing.hello .integrations {
    padding: 80px;
}

.portico-landing.hello .integrations .content {
    margin-left: 50px;
}

.portico-landing.hello .integrations .integration-icons {
    width: 100%;
    margin: 20px 0;
    text-align: center;
}

.portico-landing.hello .integrations .integration-icons .group {
    display: inline-block;
    vertical-align: top;
    width: 155px;
    height: 220px;
    padding: 0 5px;
    transition: all 0.3s ease;
    margin: 10px 5px;
    color: hsl(219deg 23% 33%);
    border-radius: 5px;
    border: 1px solid hsl(206deg 44% 93%);
}

.portico-landing.hello .integrations .integration-icons .group:hover {
    border: 1px solid hsl(170deg 47% 53%);
}

.portico-landing.hello .integrations .integration-logo {
    margin-top: 20px;
    width: 80px;
}

.portico-landing.hello .integrations .integration-name {
    margin-top: 20px;
    font-size: 22px;
    font-weight: 400;
}

.portico-landing.hello .integrations .integration-description {
    width: 120px;
    margin: 0 auto 20px;
    font-weight: 400;
    font-size: 14px;
}

.portico-landing.hello .call-to-action-bottom {
    position: relative;
    padding: 50px 100px 0;

    @media (width <= 768px) {
        padding: 50px 10px 0;
    }
    margin-top: 0;
}

.portico-landing.hello .call-to-action-bottom .styled-button {
    display: table;
    margin: 20px auto 0;
    padding: 10px 20px;
    font-size: 1em;
    font-weight: 600;
}

.portico-landing.hello .call-to-action-bottom h1 {
    text-align: center;
    margin-top: 20px;
}

.portico-landing.hello .call-to-action-bottom .zulip-octopus {
    margin: 15px auto 50px;
    width: 32px;
    height: 30px;
    background-image: url("../../images/landing-page/zulip-octopus.png");
    background-size: cover;

    filter: invert(0.9);
}

/* -- apps page -- */
.portico-landing.apps {
    padding-top: 0;
}

.portico-landing.apps .main,
.portico-landing.features-app .main {
    background-color: hsl(0deg 0% 100%);
}

.portico-landing.apps .hero {
    position: relative;

    padding: 100px 50px 50px;
    background: linear-gradient(
        35deg,
        hsl(197deg 100% 16%),
        hsl(166deg 45% 49%)
    );
    height: 600px;

    color: hsl(0deg 0% 100%);

    overflow: hidden;
}

.portico-landing.apps .hero .inner-content {
    max-width: 1600px;
    margin: 0 auto;
}

.portico-landing.apps .hero h1 {
    font-size: 3em;
    margin-bottom: 0;
    margin-top: 0;
}

.portico-landing.apps .hero #waves {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;

    background-image: url("../../images/landing-page/apps/waves.svg");
    background-size: cover;
    background-repeat: no-repeat;
}

.portico-landing.apps .hero .info,
.portico-landing.apps .hero .image {
    position: relative;

    width: 50%;
    float: left;
    height: 100%;

    z-index: 1;
}

.portico-landing.apps .hero .image img {
    border-radius: 4px 4px 0 0;
}

.portico-landing.apps .hero .info .cta {
    text-shadow: 0 0 60px hsl(0deg 0% 0% / 30%);
    max-width: 600px;
}

.portico-landing.apps .hero .image img.app-screenshot-mobile {
    height: 85%;
}

.portico-landing.apps .hero .info .flex,
.portico-landing.apps .hero .image .flex {
    height: 500px;
    min-height: 0;
}

.portico-landing.apps .hero .info .flex {
    width: 90%;
}

.portico-landing.apps .hero .info .button {
    display: inline-block;
    padding: 10px 20px;

    font-size: 1em;
    font-weight: 600;
}

.portico-landing.apps .other-apps {
    background-color: hsl(0deg 0% 100%);
    padding: 50px 50px 120px;

    text-align: center;
}

.portico-landing.apps .other-apps h2 {
    width: 600px;
    margin: 0 auto;

    text-align: center;
}

.portico-landing.apps .other-apps .apps {
    display: inline-block;
    margin: 50px 0 0;
}

.portico-landing.apps .other-apps .apps .icon {
    vertical-align: top;

    width: 50px;
    padding: 18px 30px;
    border-radius: 70px;

    /* Reset color since we don't want default link styling. */
    color: hsl(0deg 0% 27%);

    font-size: 3em;
    text-align: center;

    transition: all 0.2s ease;
}

.portico-landing.apps .other-apps .apps .icon:hover {
    background: linear-gradient(-45deg, hsl(0deg 0% 83%), hsl(0deg 0% 98%));
}

.portico-landing.apps .other-apps .apps .icon.fa-mobile-phone {
    font-size: 4em;
    padding: 14px 30px;
}

.portico-landing.apps .other-apps .apps .icon.fa-terminal {
    padding: 12px 30px;
}

.portico-landing.apps .other-apps .apps .icon.fa-mobile-phone::after {
    margin-top: 1px;
}

.portico-landing.apps .other-apps .apps .icon::after {
    content: attr(data-label);
    display: block;

    font-size: 0.8rem;
    font-weight: 600;
    font-family: "Source Sans 3", sans-serif;
    margin-top: 10px;
}

.download-from-google-play-store img {
    height: 42px;
    padding: 15px 0;
}

.download-from-apple-app-store img {
    height: 42px;
    padding: 15px 0;
}

/* -- /for/open-source/ -- */
.portico-landing.why-page {
    padding-top: 0;
    color: hsl(223deg 6% 25%);
}

.portico-landing.why-page .main {
    max-width: 800px;
}

.portico-landing.why-page .hero {
    padding: 200px 50px 100px;

    @media (width < 900px) {
        padding: 200px 0 100px;
    }

    &.empty-hero {
        padding: 50px 50px 70px;
    }

    background-color: hsl(153deg 32% 55%);
    color: hsl(0deg 0% 100%);
}

.portico-landing.why-page .hero.small-hero {
    padding: 120px 50px 30px;
}

.portico-landing.why-page .hero h1 {
    position: relative;
    margin: 0 0 20px;

    font-size: 3.5em;
    font-weight: 300;
}

.portico-landing.why-page .hero p {
    width: 70%;
    margin: 0 auto;

    font-size: 1.3em;
    text-align: center;

    opacity: 0.9;
}

.portico-landing.why-page .markdown {
    font-size: 1.1rem;
}

.portico-landing.why-page .main blockquote {
    background-color: hsl(0deg 0% 100%);
    border-color: hsl(168deg 24% 51%);
    padding: 20px 30px;
    margin-top: 20px;
    font-size: 1.05em;

    & p {
        line-height: 1.5;
        margin: 0;
        font-weight: 400;
        color: hsl(220deg 23% 33%);
    }

    & p:last-child {
        margin-top: 10px;
    }
}

.portico-landing.why-page .main img {
    display: block;
    margin: 0 auto;
    max-width: 100%;
    box-shadow: none;
    border: none;
}

.portico-landing.why-page .main .slack-image {
    width: 500px;
}

.portico-landing.why-page .main .zulip-topics-image {
    width: 300px;
}

.portico-landing.why-page .main .zulip-reply-later-image {
    width: 600px;
}

.portico-landing.why-page .photo-description {
    position: relative;
    top: -40px;
    height: 0;

    font-size: 0.8em;
    font-weight: normal;
    line-height: 100%;
    color: hsl(0deg 0% 53%);
}

.portico-landing.why-page .team h2 {
    margin-top: 20px;
}

.portico-landing.why-page .bg-events {
    position: relative;

    background-image: url("../../images/landing-page/events/for-events.jpg");
    background-size: cover;
    background-position: center;
}

.portico-landing.why-page .bg-education {
    position: relative;

    background-image: url("../../images/landing-page/education/for-education-cover.jpg");
    background-size: cover;
    background-position: center;
}

.portico-landing.why-page .bg-companies {
    position: relative;

    background-image: url("../../images/landing-page/education/companies-laptop.jpg");
    background-size: cover;
    background-position: center;

    .bg-dimmer {
        background-color: hsl(224deg 52% 12% / 75%);
    }
}

.portico-landing.why-page .bg-pycon {
    position: relative;

    background-image: url("../../images/landing-page/pycon.jpg");
    background-size: cover;
    background-position: center;
}

.portico-landing.why-page .bg-pycon.drone {
    background-image: url("../../images/landing-page/pycon-drone.jpg");
}

.portico-landing.why-page .bg-pycon.mit {
    background-image: url("../../images/landing-page/mit-lobby-7.jpg");
}

.portico-landing.why-page .bg-pycon.security {
    background-image: url("../../images/landing-page/security.jpg");
}

.portico-landing.why-page .bg-pycon.why-zulip {
    background-image: url("../../images/landing-page/why-zulip/why-zulip-threads.jpg");
}

.portico-landing.why-page .bg-dimmer {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;

    background-color: hsl(224deg 52% 12% / 70%);

    z-index: 0;
}

.portico-landing.why-page .bg-pycon .content {
    position: relative;
    z-index: 1;
}

.portico-landing.why-page .testimonials {
    background-color: hsl(168deg 43% 24%);
    color: hsl(0deg 0% 100%);
    margin-bottom: 40px;
}

.portico-landing.why-page .testimonials .quote-container {
    width: 98%;
    margin: 30px auto 20px;
    padding-left: 2%;

    font-size: 1.2rem;
}

.portico-landing.why-page .testimonials .carousel-quotes {
    width: 60%;
    margin: auto;
}

.portico-landing.why-page .testimonials .carousel-inner {
    width: 100%;
    left: -2%;
}

.portico-landing.why-page .testimonials blockquote::before {
    content: "“";
    margin-left: -10px;
    margin-right: -3px;
}

.portico-landing.why-page .testimonials blockquote::after {
    content: "”";
}

.portico-landing.why-page .testimonials blockquote + cite {
    display: block;
    margin-top: 5px;
    margin-bottom: 30px;

    color: hsl(0deg 0% 100%);
    opacity: 0.7;
    font-weight: 400;
    line-height: 140%;
}

.portico-landing.why-page .testimonials blockquote {
    padding: 0;

    font-weight: 400;
    line-height: 1.6;
    text-align: left;
    border: none;

    opacity: 0.8;
}

/* -- hello page styling -- */
.portico-landing.hello .apps .screen {
    display: inline-block;
    margin: 0 10px;
    text-align: left;
}

.portico-landing.hello .apps .screen.ios {
    width: 200px;
    height: 350px;
    padding: 30px 0;
    border-radius: 20px;

    transform: translateY(50px);

    background-color: hsl(0deg 0% 100%);
}

.portico-landing.hello .apps .screen.android {
    width: 200px;
    height: 370px;
    padding: 10px 0 30px;
    border-radius: 20px;

    transform: translateY(-110px);

    background: linear-gradient(
        90deg,
        hsl(0deg 0% 27%) 0%,
        hsl(0deg 0% 33%) 8%,
        hsl(0deg 0% 33%) 92%,
        hsl(0deg 0% 27%) 100%
    );
}

.portico-landing.hello .apps .screen .center-page {
    height: calc(100% - 20px);
}

.portico-landing.hello .apps .screen .center-page .message-feed {
    margin-top: 10px;
}

.portico-landing.hello .apps .screen.ios::before {
    top: 17px;
    left: calc(50% - 20px);

    width: 40px;
    height: 5px;
    background-color: hsl(0deg 0% 80%);
}

.portico-landing.hello .apps .screen.ios::after {
    top: auto;
    bottom: 7px;
    left: calc(50% - 12.5px);
    background-color: hsl(0deg 0% 80%);
}

.portico-landing.hello .apps .screen.android::before {
    content: none;
}

.portico-landing.hello .apps .screen.android::after {
    top: auto;
    bottom: 10px;
    left: calc(50% - 17.5px);

    border-radius: 8px;
    background-color: hsl(0deg 0% 13%);
    width: 35px;
    height: 20px;
}

.portico-landing.hello .apps .screen.ios .main-page {
    border-color: hsl(0deg 0% 87%);
}

.portico-landing.hello .apps .screen.android .main-page {
    border-color: hsl(0deg 0% 13%);
}

/* -- gradients -- */
.gradients {
    width: 100%;
    position: absolute;
    top: 0;
    z-index: 1;
}

.gradients .gradient {
    position: absolute;
    left: 0;
    width: 100%;
    height: 1100px;
}

.gradients .gradient.dark-blue {
    background: linear-gradient(
        10deg,
        hsl(196deg 58% 14% / 0%) 50%,
        hsl(196deg 58% 14% / 70%)
    );
}

.gradients .gradient.green {
    background: linear-gradient(
        -25deg,
        hsl(156deg 47% 47% / 0%) 40%,
        hsl(156deg 47% 47%)
    );
}

.gradients .gradient.blue {
    background: linear-gradient(
        25deg,
        hsl(196deg 38% 51% / 0%) 40%,
        hsl(196deg 38% 51%)
    );
}

.gradients .gradient.sunburst {
    background: linear-gradient(
        5deg,
        hsl(49deg 71% 68% / 0%) 20%,
        hsl(49deg 71% 68%)
    );
}

.gradients .gradient.white-fade {
    background: linear-gradient(
        0deg,
        hsl(0deg 0% 100%) 0%,
        hsl(0deg 0% 98% / 0%) 40%
    );
}

/* -- pricing css -- */
.portico-landing.plans .main {
    width: 100%;
}

.portico-landing.plans .main .padded-content > h1 {
    text-align: center;
    font-size: 2.5em;
    margin: 0;

    color: hsl(0deg 0% 100%);
}

.portico-landing.plans .main .padded-content > h2 {
    text-align: center;

    font-size: 1.5em;

    margin-bottom: 50px;

    color: hsl(0deg 0% 100%);
}

.pricing-model .pricing-container {
    text-align: center;
}

.pricing-model .pricing-container .block {
    display: inline-block;
    margin: 40px 20px 20px;
}

.pricing-model .pricing-container .block .plan-title {
    padding: 10px;
    margin-bottom: 3px;

    color: hsl(0deg 0% 100%);

    font-size: 2em;
    font-weight: 300;
}

.pricing-model .pricing-container .price-box {
    position: relative;
    display: inline-block;
    vertical-align: bottom;
    margin: 0;
    width: 300px;
    height: 500px;

    box-shadow: 0 0 10px hsl(0deg 0% 0% / 10%);

    text-align: left;
    background-color: hsl(0deg 0% 100%);

    transition-property: all;
    transition-duration: 0.3s;
    transition-timing-function: ease;
}

.pricing-model .pricing-container .text-content {
    margin: 18px;
}

.pricing-model .padded-content .text-header .text-content h1 {
    margin-top: 0;
}

.pricing-model .pricing-container .text-content h2 {
    font-size: 1.5em;
    font-weight: 400;
    margin-bottom: 0;

    text-align: left;
}

.pricing-model .pricing-container hr {
    border: none;
    border-bottom: 2px solid hsl(170deg 47% 53%);
    margin: 15px 0;
}

.pricing-model .pricing-container .text-content .description {
    font-size: 0.9em;
    font-weight: 400;
    color: hsl(0deg 0% 53%);
}

.pricing-model .pricing-container ul.feature-list {
    list-style: none;
    padding: 0;
    margin: 0;
}

.pricing-model .pricing-container ul.feature-list li {
    position: relative;
    padding: 10px 0 10px 25px;

    font-size: 0.9em;
    font-weight: 500;
}

.pricing-model .pricing-container ul.feature-list li::before {
    content: " ";
    position: absolute;
    top: 10px;
    left: 0;
    width: 20px;
    height: 18px;

    background-image: url("../../images/checkbox-green.svg");
    background-size: contain;
    background-position: center;
    background-repeat: no-repeat;

    filter: invert(0.3);
}

.pricing-model .pricing-container .bottom {
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 150px;

    background-color: hsl(0deg 0% 93%);
}

.pricing-model .pricing-container .text-content .price::before {
    content: "$";
    position: relative;
    vertical-align: top;
    top: 7px;
    left: -3px;

    font-size: 2rem;
    font-weight: 300;
    color: hsl(0deg 0% 53%);
}

.pricing-model .pricing-container .text-content .price {
    display: inline-block;
    margin-right: 2px;

    font-size: 3.5em;
    font-weight: 600;
    line-height: 0.8;
    margin-top: 4px;
}

.pricing-model .pricing-container .bottom .details {
    display: inline-block;
    vertical-align: top;
    margin-left: 8px;
    margin-top: 4px;

    font-size: 0.9em;
    font-weight: 400;
    color: hsl(0deg 0% 53%);

    text-align: left;
    white-space: nowrap;
}

.pricing-model .pricing-container .bottom .button {
    margin-top: 24px;
    display: block;
    text-align: center;

    font-size: 0.9em;

    transition: all 0.3s ease;
}

.pricing-model .pricing-container .price-box:focus {
    outline: none;
}

.pricing-model .pricing-container .price-box:focus .button {
    box-shadow: 0 0 25px hsl(169deg 48% 60%);
    animation: box-shadow-pulse 2s infinite;
}

.pricing-model .pricing-container .text-content .standard-price-box {
    display: flex;
    height: 55px;

    .pricing-period {
        color: hsl(0deg 0% 27%);
    }
}

.pricing-model .pricing-container .text-content .price .price-cents {
    font-size: 0.4em;
    vertical-align: top;
    position: relative;
    top: 6px;
}

.plans_faq_questions {
    background: transparent;
    padding: 20px 0;
    margin: auto;

    &.plans_top_faq {
        font-size: 17px;
        font-weight: 400;
        color: hsl(0deg 0% 53%);
        padding-top: 0;

        & p {
            padding: 10px;
        }

        & p:first-child {
            margin-top: -20px;
        }

        & p:last-child {
            margin-bottom: 30px;
        }
    }

    & p {
        width: 80%;
        margin: auto;
        text-align: center;

        @media (width <= 1100px) {
            text-align: left;
        }
    }
}

.text-content .pricing-details {
    padding: 15px 0;
    height: 25px;

    font-weight: 400;
    color: hsl(0deg 0% 53%);
    font-style: italic;
    text-align: center;

    &.multi-line {
        padding: 5px 0 25px;
    }
}

.portico-landing.jobs h2 {
    line-height: 1.4;
    margin: 20px 0 5px;
}

.portico-landing.jobs h3 {
    line-height: 1.4;
    margin: 20px 0 7px;
}

.portico-landing.jobs .open-positions-top .padded-content {
    padding-bottom: 0;
}

.portico-landing.jobs .how-we-work .padded-content {
    padding-top: 25px;
}

.portico-landing.jobs .what-were-building {
    background-color: hsl(217deg 22% 93%);
}

@keyframes box-shadow-pulse {
    0% {
        box-shadow: 0 0 0 hsl(170deg 47% 60%);
    }

    50% {
        box-shadow: 0 0 25px hsl(170deg 47% 60% / 80%);
    }

    100% {
        box-shadow: 0 0 0 hsl(170deg 47% 60%);
    }
}

/* -- media queries -- */
@media (width <= 1426px) {
    .portico-landing.hello .integrations .integration-icons .hide-1 {
        display: none;
    }

    .portico-landing.integrations .integration-categories-sidebar {
        padding-left: 30px;
    }

    .portico-landing.integrations .integration-lozenge {
        width: 135px;
    }
}

@media (width <= 1390px) {
    .portico-landing.plans
        .pricing-container
        .block:not(:first-child)
        .responsive-title {
        color: inherit;
    }
}

@media (width <= 1376px) {
    .portico-landing.plans .price-box {
        margin: 20px;
    }
}

@media (width >= 1296px), (687px <= width <= 985px) {
    /* while there are nine, show only two rows of four. */
    .portico-landing .testimonials .company-box > div:last-of-type {
        display: none;
    }
}

@media (width <= 1295px) {
    .portico-landing.hello .apps .right-side {
        display: none;
    }

    .portico-landing.hello .apps .left-side {
        width: 100%;
    }

    .portico-landing.hello .integrations .content {
        max-width: 750px;
        margin: 0 auto;
    }

    .portico-landing.hello .integrations .integration-icons {
        max-width: 600px;
        margin: 0 auto;
    }

    .portico-landing.hello .apps .left-side .content {
        margin: 0 auto 50px;
    }

    .portico-landing .testimonials .company-box .company {
        width: calc(33% - 44px);
    }
}

@media (width <= 1100px) {
    .tour .carousel-inner img {
        &.zulip-topic,
        &.slack-overwhelming,
        &.zulip-easy {
            width: 85%;
            left: 0;
            margin-left: auto;
            margin-right: auto;
        }
    }

    .tour .carousel-inner .tour-item-header {
        margin: 0 0 30px;
    }

    .tour .carousel-control {
        &.right {
            right: 20px;
        }

        &.left {
            left: 20px;
        }
    }

    .tour .carousel-inner .zulip-slack-comparison {
        width: 650px;
        max-width: 100%;

        .comparison-zulip {
            width: 450px;
        }

        .comparison-slack {
            width: 200px;
        }
    }
}

@media (width <= 1024px) {
    .portico-landing.hello .gradients .gradient {
        height: 1400px;
    }

    .portico-landing {
        padding-top: 170px;
    }

    .portico-landing.features-app {
        & section {
            &.messages {
                display: block;
                text-align: center;

                > * {
                    display: inline-block;
                    text-align: left;
                }

                .image {
                    width: 100%;
                    margin: 0;
                }
            }
        }
    }

    .portico-landing.plans .compare .padded-content {
        width: auto;
    }
}

@media (width <= 985px) {
    .features .feature-box .text-content {
        width: 100%;
        height: auto;
        margin-bottom: 20px;
    }

    .features .feature-box .image {
        float: none;
        width: 100%;
        margin: 0;
    }

    .features .text-content .flex {
        display: block;
    }

    .portico-landing.apps .main {
        width: 100%;
        margin: 0;
    }

    .portico-landing .testimonials .carousel-quotes {
        width: 100%;
    }

    .portico-landing .testimonials .fa-chevron-right {
        right: -40px;
    }

    .portico-landing .testimonials .fa-chevron-left {
        left: -40px;
    }

    .screen .message-feed .message .content {
        top: -12px;
    }

    .portico-landing.hello .apps,
    .portico-landing.hello .integrations {
        padding: 200px 50px 80px;
    }

    .portico-landing.hello .apps .left-side .content {
        width: 100%;
        text-align: center;
    }

    .portico-landing.hello .integrations {
        width: 100%;
        padding: 80px 0;
    }

    .portico-landing.hello .integrations .content {
        padding: 0 50px;
    }

    .portico-landing .testimonials hr,
    .portico-landing .testimonials .company-container {
        width: 100%;
    }

    .portico-landing .testimonials .company-box .company {
        width: calc(25% - 44px);
    }

    .tour .carousel-inner img {
        &.slack-overwhelming,
        &.zulip-easy {
            width: 80%;
            left: 0;
        }
    }

    .portico-landing.hello .hero {
        & header {
            width: calc(100% - 50px);
        }
    }
}

@media (width <= 906px) {
    .portico-landing.features-app {
        & section {
            &.notifications {
                padding: 50px 10px;

                .image-block {
                    display: none;
                }
            }
        }
    }

    .portico-landing .testimonials .quote-container {
        width: 96%;
        padding-left: 4%;
    }

    .portico-landing .testimonials .carousel-inner {
        left: -4%;
    }
}

@media (width <= 830px) {
    .portico-landing.hello .apps .left-side .platform-icons .group {
        margin: 50px 30px;
        display: block;
    }

    .portico-landing.hello .tour .carousel-inner .item-container {
        width: 85%;
    }

    .tour .carousel-control {
        font-size: 1.2em;

        &.right {
            right: -10px;
        }

        &.left {
            left: -10px;
        }
    }

    .tour .carousel-inner .zulip-slack-comparison {
        width: 100%;

        .comparison-zulip {
            width: 65%;
        }

        .comparison-slack {
            width: 35%;
        }
    }

    .tour .carousel-inner .tour-item-header {
        font-size: 1.1em;
    }
}

@media (width <= 768px) {
    .portico-landing.hello .open-source {
        .flex {
            display: block;
        }

        & img {
            display: block;
            width: 300px;
            margin: 0 auto;
        }

        .il-block {
            width: 75%;
        }
    }

    .main {
        width: auto;
    }

    .portico-landing.why-page .main {
        width: auto;
        margin: 0;
    }

    .portico-landing.why-page .hero {
        padding-left: 20px;
        padding-right: 20px;
        font-size: 0.6em;
    }

    .portico-landing.why-page .hero p {
        font-size: 2em;
        width: 100%;
    }

    .portico-landing.why-page .padded-content {
        padding: 50px 20px;
    }

    .portico-landing.why-page .testimonials .padded-content {
        padding: 50px;
    }

    .portico-landing.why-page .testimonials .carousel-quotes {
        width: 90%;
    }

    .portico-landing.why-page .testimonials .quote-container {
        padding-left: 4%;
        font-size: 1em;
    }

    .platform.image {
        display: none !important;
    }

    .platform.description {
        width: 100% !important;
    }

    .portico-landing.hello .hero {
        & header {
            width: 600px;
        }
    }

    .portico-landing.hello .apps .left-side .content {
        width: auto;
    }

    .portico-landing.features-app {
        & section {
            padding: 0 20px;

            &.hero {
                padding: 50px;

                & h1 {
                    font-size: 3em;
                }
            }
        }
    }

    .billing-upgrade-page {
        .nav-tabs,
        .tab-content {
            font-size: 1em;
        }
    }
}

@media (width <= 1024px) {
    .portico-landing {
        padding-top: 120px;
    }

    .portico-landing.apps .hero {
        height: 350px;
    }

    .portico-landing.apps .hero h1 {
        font-size: 1.9em;
        font-weight: 400;
    }

    .portico-landing.apps .hero .info .flex,
    .portico-landing.apps .hero .image .flex {
        height: 200px;
        min-height: 0;
        width: 100%;
    }

    .portico-landing.apps .other-apps {
        padding: 50px 5px 120px;
    }

    .portico-landing.apps .other-apps h2 {
        font-size: 1.5em;
        width: 100%;
    }

    .portico-landing.apps .other-apps .apps .icon {
        padding: 0 14px;
        width: 30px;
        padding-top: 8px;
        padding-bottom: 0;
        font-size: 2.3em;
    }

    .portico-landing.apps .other-apps .apps .icon.fa-mobile-phone {
        padding: 7px 10px 5px;
        width: 35px;
        font-size: 2.5em;
    }

    .portico-landing.apps .other-apps .apps .icon.fa-windows {
        font-size: 2em;
        padding: 10px 13px 2px !important;
    }

    .portico-landing.apps .other-apps .apps .icon::after {
        content: "";
    }

    .portico-landing.apps .hero .image {
        display: none;
    }

    .portico-landing.apps .hero .info {
        width: 100%;
    }

    .main {
        width: calc(100% - 50px);
        margin: 0 auto;
    }

    .portico-landing.hello .hero {
        padding-bottom: 100px;

        .waves {
            height: 450px;
        }

        & header {
            width: auto;
        }
    }

    .portico-header .content > ul::before {
        content: "Zulip";
        display: block;
        margin-top: 25px;
        padding-top: 5px;
        margin-left: 10px;

        width: 100px;
        height: 40px;

        font-size: 1.5rem;
        line-height: 30px;
        text-align: right;
        color: hsl(0deg 0% 27%);

        background-size: 40px auto;
        background-image: url("../../images/zulip-logo.svg");
        background-repeat: no-repeat;
    }

    .portico-header .dropdown ul {
        width: 100%;
        height: auto;
        margin: 42px 0 0;
        font-size: 0.8em;
    }

    .portico-landing.apps .main ul.sidebar {
        display: block;
        text-align: center;
        margin-bottom: 10px;
    }

    .portico-landing.apps .main ul.sidebar li {
        display: inline-block;
        padding: 10px;
        width: 80px;
        text-align: center;
        border-radius: 4px;
    }

    .portico-landing .testimonials .company-box .company {
        margin: 10px;
        width: calc(33% - 24px);
    }

    .tour .carousel-control {
        font-size: 1.1em;

        .right {
            right: -30px;
        }

        .left {
            left: -30px;
        }
    }

    .tour .carousel-inner .zulip-slack-comparison img {
        max-width: 90%;
    }

    .portico-landing.hello .tour .carousel-inner .item-container {
        height: 450px;
    }

    .tour .carousel-inner .call-to-action {
        margin: 10px auto;
    }
}

@media (width <= 640px) {
    .portico-landing.hello .integrations .integration-icons .group {
        margin: 10px 16px 0;
    }

    .portico-landing.features-app {
        & section {
            &.keyboard-shortcuts {
                & img {
                    &.overflow-wave {
                        top: -100px;
                    }
                }
            }
        }
    }
}

@media (width <= 550px) {
    .portico-landing.features-app {
        & section {
            &.hero {
                padding: 50px 20px 20px;
            }

            &.messages {
                padding: 0 20px;

                & h2 {
                    font-size: 2em;
                }

                .features {
                    .feature-block {
                        margin: 20px 0;
                    }
                }
            }
        }
    }

    .portico-landing .tour {
        max-width: 100%;
    }

    .portico-landing.hello .tour .carousel-inner .item-container {
        height: 400px;
    }

    .tour .carousel-control {
        top: 100%;
    }

    .tour .carousel-inner .zulip-slack-comparison {
        .comparison-zulip {
            width: 60%;
        }

        .comparison-slack {
            width: 38%;
        }

        .caption {
            font-size: 90%;
        }

        & img {
            max-width: 100%;

            &.zulip-streams {
                max-width: 140px;
            }

            &.zulip-streams-selected {
                max-width: 95%;
            }
        }
    }

    .tour .carousel-inner .tour-explanation {
        opacity: 0.8;
        font-size: 90%;
        text-align: left;
    }

    .billing-upgrade-page {
        .payment-schedule {
            .box {
                width: 100px;
                height: 80px;
            }
        }
    }
}

@media (width <= 450px) {
    .portico-landing.plans .price-box {
        display: inline-flex;
        flex-direction: column;
        min-height: 500px;
        height: auto;
        max-width: 300px;
        width: auto;
        margin: 10px 0;
    }

    .pricing-model .pricing-container .text-content {
        flex: 1;
    }

    .pricing-model .pricing-container .bottom {
        position: static;
        height: auto;
    }

    .portico-landing.hello .hero {
        padding: 60px 5px 40px;
    }

    .portico-landing.hello header {
        padding: 0 45px;
    }

    .portico-landing.hello .integrations .content header {
        padding: 0;
    }

    .portico-landing.hello .integrations .integration-icons .group {
        margin: 4px 2px;
    }

    .main {
        width: 100%;
    }

    .portico-landing.plans .compare .padded-content {
        padding: 20px;
    }

    .portico-landing.plans .pricing-container .block {
        margin: 0;
    }

    .tour .carousel-inner .mobile-hide,
    .tour .carousel-inner img.mobile-hide,
    .tour .carousel-inner img.centered-image.mobile-hide {
        display: none;
    }

    .tour .carousel-inner .mobile-show,
    .tour .carousel-inner img.mobile-show,
    .tour .carousel-inner img.centered-image.mobile-show {
        display: block;
    }

    .main .padded-content {
        padding: 20px;
    }

    /* the gradients leave the bottom of the text and the button white so we
       want to have the gradients stay darker for longer.
    */
    .gradients .gradient.green {
        background: linear-gradient(
            -25deg,
            hsl(156deg 47% 47% / 0%) 10%,
            hsl(156deg 47% 47%) 80%
        );
    }

    .gradients .gradient.blue {
        background: linear-gradient(
            25deg,
            hsl(196deg 38% 51% / 0%) 10%,
            hsl(196deg 38% 51%) 80%
        );
    }

    .gradients .gradient.sunburst {
        background: linear-gradient(
            5deg,
            hsl(49deg 71% 68% / 0%) 20%,
            hsl(49deg 71% 68%) 80%
        );
    }

    .features-app .gradients .gradient {
        height: 700px;
    }
}

@media (width <= 375px) {
    .portico-landing.hello .integrations .integration-icons .group {
        width: 130px;
        height: 215px;
    }

    .portico-landing.hello .integrations .integration-icons .integration-logo {
        width: 60px;
    }

    .portico-landing.integrations .integration-categories-dropdown {
        width: 323px;
    }

    .portico-landing.features-app {
        & section {
            &.keyboard-shortcuts {
                & img {
                    &.overflow-wave {
                        top: -92px;
                    }
                }
            }
        }
    }
}

@media (width <= 360px) {
    .portico-landing.features-app {
        & section {
            .keyboard-shortcuts {
                & img {
                    &.overflow-wave {
                        top: -88px;
                    }
                }
            }
        }
    }
}

/* For iPhone 5/SE device */
@media (width <= 320px) {
    .portico-landing.features-app {
        & section {
            .keyboard-shortcuts {
                & img {
                    &.overflow-wave {
                        top: -78px;
                    }
                }
            }
        }
    }
}

@media (width <= 313px) {
    .portico-landing .testimonials .quote-container {
        width: 93%;
        padding-left: 7%;
    }

    .portico-landing .testimonials .carousel-inner {
        left: -7%;
    }
}

#download-android-apk,
#download-mac-arm64 {
    display: inline-block;
    color: hsl(0deg 0% 100%);
    font-size: 13px;
    padding-left: 10px;
}

.feature-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 50px 4vw 10px;

    .feature-half {
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .md-hide {
        display: none;
    }

    .md-display {
        display: block;
    }

    @media (width <= 768px) {
        .feature-text {
            margin-bottom: 10px;
        }

        .twitter-tweet {
            margin: 30px auto !important;
        }
    }

    @media (width >= 768px) {
        display: grid;
        grid-column-gap: 5%;
        grid-template-columns: 43% auto;
        max-width: 1300px;
        align-items: center;
        justify-items: center;
        margin: auto;

        .alternate-grid& {
            grid-template-columns: auto 43%;
        }

        .feature-half {
            display: block;
        }

        .md-display {
            display: none !important;
        }
    }

    .feature-text {
        & h1 {
            font-size: 30px;
            font-weight: 600;
        }

        & ul {
            list-style: none;
            margin-left: 0;
        }

        & ul li {
            margin-bottom: 15px;

            &::before {
                float: left;
                background-repeat: no-repeat;
                content: "";
                width: 18px;
                height: 18px;
                margin-right: 5px;
                margin-top: 4px;
                background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 24 24"><path d="M12 0c-6.627 0-12 5.373-12 12s5.373 12 12 12 12-5.373 12-12-5.373-12-12-12zm-1.25 17.292l-4.5-4.364 1.857-1.858 2.643 2.506 5.643-5.784 1.857 1.857-7.5 7.643z"/></svg>');
            }

            .list-content {
                margin-left: 22px;
                line-height: 1.6;
                font-size: 18px;
            }
        }
    }

    .feature-image {
        & img,
        div.quote {
            width: 400px;
        }

        @media (width < 1024px) {
            & div.quote {
                width: 300px;
            }
        }

        @media (width < 768px) {
            & div.quote {
                width: auto;
            }
        }
    }

    .feature-icon {
        & img,
        div.quote {
            width: 100px;
        }
    }

    .topics-image {
        border: solid 2px hsl(0deg 0% 60%);
    }
}

.twitter-tweet {
    margin: auto;
}

.discounts-section {
    text-align: center;

    & header {
        & b {
            font-weight: 600;
            color: hsl(169deg 45% 43%);
        }
    }
}

.register-buttons {
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    margin: 20px;
}

/* Common button styles */
.register-now,
.register-now:visited {
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    font-size: 15px;
    margin: 10px 20px;
    float: left;
    width: 200px;
    border: 2px solid;
    border-radius: 4px;
    background: none;
    color: hsl(169deg 45% 43%);
    vertical-align: middle;
    position: relative;
    z-index: 1;
    backface-visibility: hidden;
    -moz-osx-font-smoothing: grayscale;
    letter-spacing: 2px;
    text-transform: uppercase;
    overflow: hidden;
    transition: border-color 0.3s, background-color 0.3s;
    transition-timing-function: cubic-bezier(0.2, 1, 0.3, 1);
    font-weight: 800;
    padding: 15px 5px;

    &:focus {
        outline: none;
    }

    & p {
        font-weight: 600;
        margin-bottom: 0;
    }

    &:hover {
        border-color: hsl(169deg 45% 43%);
        background-color: hsl(170deg 47% 53%);
        color: hsl(0deg 0% 100%);
    }
}

.quote {
    background: hsl(218deg 46% 43%);
    padding: 1em;
    border-radius: 1em;
    font-weight: 400;
    margin: 40px 5px;
    display: flex;
    flex-direction: column;

    & a {
        color: hsl(0deg 0% 100%);

        &.case-study-link {
            margin-left: 20px;
            text-decoration: underline;
        }

        &:hover {
            text-decoration: underline;
        }
    }

    .author,
    blockquote {
        color: hsl(0deg 0% 100%);
        margin: 5px 20px 20px;
    }

    & blockquote {
        font-size: 18px;
    }

    & blockquote::before {
        font-size: 20px;
        font-weight: 800;
    }

    & cite {
        font-style: normal;
    }
}

.intro_quote {
    & blockquote {
        font-size: 17px;
        font-weight: 400;
        color: hsl(223deg 6% 25%);
        border-left: 6px solid hsl(218deg 46% 43%);
        position: relative;
        background: hsl(0deg 0% 93%);
        padding: 20px;
    }

    & blockquote::after {
        content: "";
    }

    .author {
        padding-top: 20px;
    }
}

.case-study-page,
.solutions-page {
    .bottom-register-buttons.extra_margin_before_footer {
        margin-bottom: 60px;
    }

    .hero-text {
        position: relative;
        width: 80%;
        max-width: 700px;
        margin: 40px auto;
        font-size: 20px;
        text-align: center;
        font-weight: bolder;
        opacity: 0.9;
    }

    .hero {
        & a {
            color: hsl(170deg 76% 64%);
        }
    }

    .hero-buttons {
        display: flex;
        flex-flow: row wrap;
        justify-content: center;

        & a {
            color: hsl(170deg 47% 33%);
            font-weight: 600;
            font-size: 15px;
            margin: 10px;

            &:hover {
                color: hsl(0deg 0% 100%);
                background-color: hsl(170deg 47% 33%);
                border-color: hsl(170deg 47% 33%);
            }
        }
    }

    .feature-end {
        @media (width >= 768px) {
            margin: 10px;
        }

        & h1 {
            margin-top: 20px;
            text-align: center;
            font-weight: 600;
            margin-bottom: 10px;
            padding-bottom: 0;
        }

        & ul {
            margin: auto;
            max-width: 800px;
            padding: 30px;
        }

        & p {
            margin: auto;
            max-width: 800px;
            padding: 30px;
        }
    }

    .price-asterisk {
        text-align: center;
        margin-top: 0 !important;
        padding-top: 0 !important;
        font-size: 15px;
        opacity: 0.8;
        max-width: 560px !important;
    }
}

.bottom-register-buttons {
    max-width: 800px;
    margin: auto;

    & h1 {
        text-align: center;
        font-weight: 600;
        margin-bottom: 0;
        padding-bottom: 0;
    }

    .hero-buttons {
        margin: 20px;
    }
}

.solutions-page .pricing-model {
    .padded-content {
        padding-bottom: 10px;
    }

    .pricing-container {
        display: flex;
        flex-flow: row wrap;
        justify-content: center;
    }

    .price-box {
        margin: 10px;
    }
}

.for-education.pricing-model {
    .pricing-details {
        color: inherit;
        font-style: inherit;
    }

    .price-box {
        height: 625px;

        .bottom {
            height: 275px;

            .standard-register-button {
                margin-top: 10px;
            }

            .free-text {
                margin-top: 90px;

                .pricing-details {
                    font-size: 34px;
                }

                & a {
                    margin-top: 76px;
                }
            }

            .standard-price-box {
                flex-flow: row wrap;
                height: 90px;
                font-size: 15px;

                &:first-child {
                    padding-bottom: 10px;
                }

                & p {
                    padding: 0;
                    margin: 0 0 -10px;
                    width: 100%;
                    text-align: center;
                    font-weight: 550;
                    color: hsl(169deg 46% 33%);
                }
            }
        }
    }
}

.portico-landing.why-page.case-study-page {
    .bg-dimmer {
        background-color: hsl(224deg 52% 12% / 86%);
    }
}

.feature-intro {
    max-width: 800px;
    margin: 50px auto 0;
    padding: 0 4vw;

    & h1 {
        font-size: 36px;
        font-weight: 600;
    }
}

.for-companies {
    .feature-end {
        margin-top: 50px;

        .description {
            margin: 0 10px;
        }

        & p {
            padding: 10px;
        }

        .intro_quote {
            margin: 20px auto 0;
            max-width: 800px;
        }

        .pricing-model {
            @media (width >= 768px) {
                .price-box {
                    margin: 10px;
                }
            }

            .padded-content {
                padding: 20px;
            }

            .plan-title {
                color: hsl(0deg 0% 0%);
            }
        }
    }
}

.mirror-image {
    transform: scaleX(-1);
}

.why-zulip {
    .discounts-section {
        margin: 30px;

        & h1 {
            font-weight: 700 !important;
            font-size: 26px !important;
        }
    }
}

.portico-landing.why-page .hero.why-zulip {
    padding-bottom: 120px;

    .bg-dimmer {
        background-color: hsl(224deg 52% 12% / 85%);
    }

    .padded-content {
        padding-top: 0;
        padding-bottom: 10px;
    }

    @media (width <= 768px) {
        .register-buttons {
            display: none;
        }
    }

    .discounts-section .register-buttons a {
        color: hsl(169deg 71% 64%);

        &:hover {
            color: hsl(0deg 0% 100%);
        }
    }
}

.why-zulip,
.hello {
    .register-buttons {
        max-width: 800px;
        margin: auto;
        margin-top: 30px;

        & a {
            min-height: 40px;
            padding: 7px 0;
        }
    }

    @media (width <= 768px) {
        .register-buttons {
            & a {
                margin: 10px calc(5vw - 10px);
                width: clamp(130px, 40vw, 200px);
                font-size: 13px;
            }
        }
    }
}

.self-hosting-page {
    & p {
        font-size: 18px !important;
    }

    .hero-buttons {
        margin-top: 30px;
    }

    .alternative-features {
        .feature-container {
            padding: 30px;

            &:nth-child(even) {
                background: hsl(171deg 49% 39% / 21%);
                border-radius: 10px;
            }
        }

        .feature-icon img {
            width: 100%;
        }
    }

    .triangle {
        position: absolute;
        top: 0;
        left: 0;
        width: 0;
        height: 0;
        border-style: solid;
        border-width: 150px 100vw 0 0;
        border-color: hsl(0deg 0% 100%) transparent transparent transparent;
    }

    .quote {
        position: relative;
        margin: 0;
        margin-top: 50px;
        padding: 50px;
        padding-top: 200px;
        border-radius: 0;
        background: linear-gradient(
            145deg,
            hsl(191deg 56% 55%),
            hsl(169deg 65% 42%)
        );

        & blockquote {
            max-width: 700px;
            margin: auto;
            font-size: 24px;

            .author {
                font-size: 18px;
            }
        }
    }

    .feature-grid {
        display: flex;
        flex-direction: column;
        width: 100%;
        margin: 0;
        background: hsl(171deg 49% 39% / 21%);
        padding: 50px 0;

        .feature-row {
            display: flex;
            flex-direction: row;
            max-width: 1000px;
            margin: auto;
            align-items: center;
            justify-content: center;
            gap: 20px;

            .feature-box {
                display: flex;
                justify-content: flex-start;
                align-items: flex-start;
                flex-direction: column;
                width: 40vw;
                height: 350px;
                box-shadow: 0 1px 1px 0 hsl(193deg 100% 7.1% / 30%),
                    1px 1px 1px 0 hsl(193deg 100% 7.1% / 15%),
                    -1px 1px 1px 0 hsl(193deg 100% 7.1% / 15%);

                background: hsl(0deg 0% 100%);
                text-align: left;
                margin: 10px 0;
                padding: 50px 30px 0;
                border-top: 5px solid hsl(171deg 49% 39%);

                @media (width < 1000px) {
                    height: 400px;
                }

                & h1 {
                    font-weight: 550;
                    font-size: clamp(24px, 2.5vw, 32px);
                }

                .feature-icon {
                    align-self: center;

                    & img {
                        max-width: 100px;
                    }
                }
            }

            @media (width < 768px) {
                flex-direction: column;

                .feature-box {
                    width: 75vw !important;
                    height: calc(600px - 35vw);
                }
            }
        }
    }

    .for-education.pricing-model .pricing-container .price-box {
        height: 525px;

        .bottom {
            height: 150px;
        }
    }

    .feature-end {
        margin: 0;

        .feature-pricing {
            padding: 50px;
            background: linear-gradient(
                180deg,
                hsl(191deg 56% 55%),
                hsl(169deg 65% 42%)
            );

            @media (width <= 540px) {
                padding: 50px 0;

                .price-box {
                    padding-bottom: 50px;
                }
            }

            & h1 {
                color: hsl(0deg 0% 100%);
            }
        }
    }
}

.try-zulip-now-page {
    .bottom-register-buttons {
        text-align: center;
        margin-bottom: 20px;
    }

    .try-now-button {
        padding: 11px 25px;
        font-size: 1.2rem;
        font-weight: 400;
        color: hsl(0deg 0% 100%);
        background: linear-gradient(
            145deg,
            hsl(191deg 56% 55%),
            hsl(169deg 65% 42%)
        );
        box-shadow: 0 3px 10px hsl(0deg 0% 0% / 20%);
        border: 0;
        width: 200px;
        height: 50px;
        outline: none;
        border-radius: 4px;

        &:visited {
            color: hsl(0deg 0% 100%);
        }

        &:hover {
            background-color: hsl(169deg 65% 42%);
            box-shadow: 0 3px 10px hsl(0deg 0% 0% / 30%);
        }
    }
}

~~~
#### integrations_dev_panel.css ####
~~~
#custom_http_headers {
    width: 100%;
    height: 60px;
    resize: vertical;
}

#dev-panel {
    margin-left: 3%;
    margin-right: 3%;
    padding: 20px 10px 15px;
    background-color: hsl(0deg 0% 100% / 48%);
    box-shadow: 0 0 40px hsl(0deg 0% 0% / 6%);

    & textarea {
        color: hsl(0deg 0% 33%);
        background-color: hsl(0deg 0% 100%);
        border-radius: 4px;
        vertical-align: middle;
        border: 1px solid hsl(0deg 0% 80%);
        padding: 4px 6px;
        margin-bottom: 10px;

        font-size: 14px;

        box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%);
        transition: border linear 0.2s, box-shadow linear 0.2s;

        &:focus {
            border-color: hsl(206.5deg 80% 62% / 80%);
            outline: 0;

            box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%),
                0 0 8px hsl(206.5deg 80% 62% / 60%);
        }

        &:read-only {
            cursor: not-allowed;
        }
    }

    & select,
    textarea,
    input {
        font-family: inherit;
    }

    & select {
        height: 30px;
        padding: 4px 6px;
        width: 220px;
        font-size: 14px;
        color: hsl(0deg 0% 33%);
        border-radius: 4px;
        border: 1px solid hsl(0deg 0% 80%);
        margin-bottom: 10px;
        cursor: pointer;
        background-color: hsl(0deg 0% 100%);
        vertical-align: middle;
    }
}

#fixture_body {
    width: 90%;
    height: 500px;
    resize: vertical;
}

#idp-results {
    width: 100%;
    height: 500px;
    resize: vertical;
    background-color: hsl(0deg 0% 100%);
}

.top-navbar {
    display: grid;
    grid-template-columns: 1fr 5fr 1fr;
}

#URL {
    width: 100%;
}

#stream_name,
#topic_name {
    width: 206px;
}

.buttons {
    display: flex;
    justify-content: space-between;
    width: 92%;
    margin-right: 2%;
}

.centerpiece {
    font-size: 30px;
    text-align: center;
}

.inline {
    display: flex;
    flex-wrap: nowrap;
    justify-content: space-between;
    margin-right: 10%;
}

.optional {
    color: hsl(0deg 0% 50%);
}

.pad-small {
    height: 100px;
    width: 100%;
}

.row1 {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-left: 2%;
    margin-right: 2%;
}

.row2 {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    margin-left: 2%;
    margin-right: 2%;
}

.row3 {
    display: flex;
    flex-flow: column wrap;
    justify-content: flex-start;
    margin-left: 2%;
    margin-right: 2%;
}

.row4 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin-left: 2%;
    margin-right: 2%;
}

~~~
#### right_sidebar.css ####
~~~
/* Width of emoji used by user to display status. */
$user_status_emoji_width: 24px;

.right-sidebar {
    & a:hover {
        text-decoration: none;
    }
}

#buddy_list_wrapper {
    position: relative;
    margin-left: 0;
    overflow: auto;
}

#user_presences {
    max-width: 95%;
    overflow-x: hidden;
    list-style-position: inside; /* Draw the bullets inside our box */

    & li {
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        list-style-type: none;
        border-radius: 4px;
        padding-right: 15px;
        padding-top: 1px;
        padding-bottom: 2px;

        .user-list-sidebar-menu-icon {
            position: absolute;
            top: 1px;
            right: 0;
            font-size: 1em;
            display: none;
            text-align: center;
            padding: 0 6px;

            & i {
                padding-right: 0.25em;
                display: inline-block;
                width: 13px;
                vertical-align: middle;
            }

            &:hover {
                display: inline;
                cursor: pointer;
                color: hsl(0deg 0% 0%) !important;
            }

            /*
            Hover does not work for touch-based devices like mobile phones.
            Hence the the icons does not appear, making the user unaware of its
            presence on such devices. The following media property displays the
            icon by default for such behaviour.
            */

            @media (hover: none) {
                display: inline;
            }
        }

        &:hover {
            .user-list-sidebar-menu-icon {
                display: inline;
                cursor: pointer;
                color: hsl(0deg 0% 53%);
            }
        }

        &:hover,
        &.highlighted_user {
            background-color: hsl(120deg 12.3% 71.4% / 38%);
        }
    }

    .user_circle {
        min-width: 8px;
        height: 8px;
        margin: 0 5px;
        display: block;
    }

    & a {
        color: inherit;
        margin-left: 0;
    }
}

.user-presence-link,
.user_sidebar_entry .selectable_sidebar_block {
    display: flex;
    overflow: hidden;

    .user-name {
        overflow: hidden;
        text-overflow: ellipsis;
    }
}

.user_sidebar_entry .selectable_sidebar_block {
    width: calc(100% - 16px);
    display: flex;
    flex-direction: row;
}

.user-name-and-status-wrapper {
    display: block;
    width: 100%;
}

.user-presence-link {
    width: calc(100% - $user_status_emoji_width);

    .status-emoji {
        top: 9px;
    }
}

.my_user_status {
    opacity: 0.5;
}

.selectable_sidebar_block {
    cursor: pointer;
}

.user_list_style_values {
    .user-name-and-status-emoji {
        display: block;
        width: 100%;
        height: 20px;

        .user-name {
            display: inline-block;
            max-width: calc(100% - $user_status_emoji_width);
            overflow-x: hidden;
            text-overflow: ellipsis;
        }

        .status-emoji {
            line-height: 20px;
            top: -2px;
        }
    }

    .status-text {
        overflow-x: hidden;
        text-overflow: ellipsis;
    }
}

.user_sidebar_entry {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;

    .user-name-and-status-emoji {
        display: flex;
    }

    .status-text {
        display: block;
        width: 170px;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        opacity: 0.75;
        font-size: 90%;
    }

    & span.status-text:not(:empty) {
        margin-top: -3px;
    }

    .unread_count {
        display: none;
        margin-top: 2.5px;
    }

    &.user-with-count .unread_count {
        display: block;
        margin-left: 4px;
    }
}

#userlist-toggle {
    display: none;
    position: absolute;
    top: 0;
    right: 0;
    text-align: center;
    vertical-align: middle;
    border-left: 1px solid hsl(0deg 0% 88%);
}

#userlist-toggle-button {
    text-decoration: none;
    color: hsl(0deg 0% 60%);
    display: block;
    width: 45px;
    height: 19px;
    padding-top: 12px;
    padding-bottom: 9px;

    &:hover {
        color: inherit;
    }
}

.right-sidebar-items:first-of-type #userlist-header {
    border-top: none;
}

#userlist-header {
    cursor: pointer;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin-right: 10px;

    #userlist-title {
        margin: 0;
    }

    #user_filter_icon {
        opacity: 0.5;
        margin-right: 5px;

        &:hover {
            opacity: 1;
            cursor: pointer;
        }
    }

    /* hovering over the userlist-header creates the same highlight effect as hovering over the user_filter_icon */
    &:hover > #user_filter_icon {
        opacity: 1;
        cursor: pointer;
    }
}

#keyboard-icon {
    position: relative;
    cursor: pointer;
    font-size: 20px;
    margin-right: 15px;
}

#sidebar-keyboard-shortcuts {
    color: inherit;
}

.right-sidebar-shortcuts {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-top: 5px;
}

@media (width < $xl_min) {
    #userlist-toggle {
        display: block;
    }
}

#user_search_section {
    & input {
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden;
        padding-right: 20px;
        width: calc(100% - 40px - 3px);
    }
}

@media (width < $sm_min) {
    #userlist-toggle {
        height: 30px;
        line-height: 30px;
    }

    #userlist-toggle-button {
        height: 30px;
        padding-top: 0;
        padding-bottom: 0;
    }
}

.right-sidebar-shortcuts .realm-description {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-right: 20px;
    width: 230px;

    .color_animated_button {
        width: 100%;
        margin-bottom: 10px;
    }

    & hr {
        width: 90%;
    }
}

~~~
#### popovers.css ####
~~~
/*
  Our Tippy popovers use the strangely named "light-border" Tippy
  theme, so this block defines the common styling for all of our Tippy
  popovers. (Tippy tooltips are defined in tooltips.css).
*/
.tippy-box[data-theme="light-border"] {
    .tippy-content {
        font-size: 14px;
    }

    /* TODO: Clean this logic up after drop Bootstrap styling */
    & ul.nav {
        /* Override default padding of tippyjs */
        margin: 0 -9px;

        /* Override bootstrap defaults */
        .nav-list > li > a {
            padding: 3px 15px;
        }

        /* Override bootstrap defaults */
        & hr {
            margin: 5px 0;
        }
    }
}

.popover {
    width: auto;
    max-width: 100%;

    & hr {
        margin-top: 5px;
        margin-bottom: 5px;
    }

    .sub_disable_btn_hint {
        padding-left: 5px;
        padding-right: 5px;
        font-size: small;
        text-align: justify;
    }
}

.popover-content {
    padding: 5px 0;
}

.popover-title {
    overflow-x: hidden;
    text-overflow: ellipsis;
    text-align: center;

    font-size: inherit;
    line-height: inherit;

    &:empty {
        display: none;
    }
}

.user_full_name,
.bot_owner {
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
}

.popover_user_name_row {
    display: flex;
    align-items: center;
}

.user_info_popover_action_buttons {
    display: flex;
    margin-left: auto;
}

.user_info_popover_manage_menu_btn {
    &:hover,
    &:focus {
        text-decoration: none;
    }
}

.user_popover_manage_menu {
    .zulip-icon {
        /* Overriding CSS margin */
        margin-right: 0;
    }
}

.info_popover_actions .custom_user_field {
    display: flex;
    align-items: center;

    .value {
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;
    }

    /* Overriding CSS from rendered_markdown.css */
    .rendered_markdown p {
        margin: 0;
    }

    /* Overriding CSS from bootstrap > nav-list. */
    .custom_profile_fields_link {
        padding-top: 0;
        padding-bottom: 0;

        &:hover {
            background-color: transparent !important;
        }

        &:focus {
            background-color: transparent !important;
        }
    }
}

.info_popover_actions .user_info_popover_manage_menu_btn {
    /* Create a larger click target around the icon. */
    padding: 0 6px;

    opacity: 0.8;

    &:hover {
        opacity: 1;
    }
}

.sp-container {
    z-index: 106;
}

.streams_popover {
    .topic-name {
        text-align: center;
        margin-top: 5px;
        margin-bottom: 5px;
    }

    .colorpicker-container {
        display: none;
        margin-right: 10px;

        .sp-container {
            background-color: hsl(0deg 0% 100%);
            cursor: pointer;
            border: none;

            .sp-palette-container {
                border-right: none;
            }

            & input {
                box-sizing: inherit; /* IE */
                box-sizing: initial;

                width: calc(100% - 13px);
            }

            & button {
                background-color: hsl(0deg 0% 100%);
                background-image: none;
                border: 1px solid hsl(0deg 0% 80%);
                border-radius: 4px;
                color: hsl(0deg 0% 25%);
                font-size: 12px;
                padding: 6px;
                text-transform: capitalize;
                text-align: center;
                text-shadow: none;
            }

            .sp-picker-container {
                border-left: solid 1px hsl(0deg 0% 88%);
            }
        }
    }

    .popover_sub_unsub_button {
        margin-top: 0;
        float: none;
    }
}

ul {
    &.info_popover_actions i,
    &.actions_popover i,
    &.streams_popover i,
    &.topics_popover i {
        display: inline-block;
        text-align: center;

        &:not(.popover_action_icon) {
            width: 14px;
        }

        &:not(.popover_action_icon, .custom_user_field i) {
            margin-right: 3px;
        }

        &.zulip-icon {
            /* These icons are different from font awesome icons,
                so they need to be aligned separately. */
            line-height: 14px;
            position: relative;

            &:not(.zulip-icon-bot) {
                top: 2px;
            }
        }
    }

    &.topics_popover {
        .topic-name {
            text-align: center;
            margin-top: 5px;
            margin-bottom: 5px;

            .fa-chevron-right {
                font-size: 12px;
            }
        }
    }

    &.info_popover_actions i.fa-edit {
        vertical-align: middle;
    }
}

.actions_popover {
    .mark_as_unread {
        .unread_count {
            /* The icon for this menu item is in the form of an unread count from
               the left sidebar. We reuse much of the shared styling,
               but need to override some of the defaults set in app_components.css. */
            display: inline;
            float: unset;
            line-height: 14px;
            font-size: 11px;
            font-weight: 550;
            margin-right: 2px;
            background-color: hsl(200deg 100% 40%);
            /* Override random undesired bootstrap style */
            text-shadow: none;
            /* Not center aligned but looks better. */
            position: relative;
            top: -1px;
        }
    }
}

/* Important note: The user info popover user_popover class is applied
   to user info popovers ONLY when they are opened from the right
   sidebar; otherwise, it will have the user-info-popover class
   instead. */
.user_popover {
    width: 240px;

    margin: -14px;
    padding: 0;

    .popover-title {
        padding: 0;
        border-color: hsl(0deg 0% 0% / 20%);
    }

    .popover_info li {
        word-wrap: break-word;
    }
}

.message-info-popover,
.user-info-popover {
    width: 240px;
    padding: 0;

    .popover-title {
        padding: 0;
        border-color: hsl(0deg 0% 0% / 20%);
    }
}

.group-info-popover {
    .manage-group a {
        text-align: center;
    }

    .group-info {
        text-align: center;

        .group-name {
            font-weight: bold;
        }
    }

    .member-list {
        position: relative;
        max-height: 300px;
        overflow-y: auto;
        list-style: none;
        margin-left: 0;

        .bot {
            color: hsl(180deg 5% 74%);
            vertical-align: top;
            width: 20px;
            padding-top: 3.5px;
            text-align: center;
        }
    }
}

.user_profile_presence,
.popover_user_presence {
    width: 8px;
    height: 8px;
    margin: 0 5px;
    display: inline-block;
    float: initial;
    position: relative;
    top: 0;
    flex-shrink: 0;
}

.bot-owner-name {
    text-decoration: underline;

    &:hover {
        cursor: pointer;
        color: hsl(200deg 100% 40%);
    }
}

.popover-avatar {
    height: 240px;
    width: 240px;
    background-size: cover;
    background-position: center;
    position: relative;

    &.guest-avatar::after {
        outline: 10px solid hsl(0deg 0% 100%);
    }

    .popover-inner {
        width: 240px;
    }
}

#user-profile-modal {
    .modal__body {
        box-sizing: border-box;
        height: 60vh;
        padding-left: 16px;
        padding-right: 16px;
    }

    .modal__header {
        justify-content: center;
    }

    .user_profile_presence {
        margin: 5px;
        vertical-align: middle;
    }

    .modal__close {
        position: absolute;
        right: 20px;
    }

    #tab-toggle {
        font-weight: initial;
        padding: 0 16px 6px;
    }

    .name {
        color: hsl(0deg 0% 20%);
        width: 120px;
        font-weight: 600;
        margin-right: 10px;
    }

    .value {
        vertical-align: top;
    }

    #exit-sign {
        font-size: 1.5rem;
        line-height: 1;
    }

    #profile-tab {
        margin: 1px 5px 0;

        & li.custom_user_field {
            display: block;
        }
    }

    .top {
        display: flex;
        justify-content: space-between;
    }

    @media (width < $ml_min) {
        .top {
            flex-direction: column-reverse;
        }
    }

    #avatar {
        display: inline-block;
        height: 180px;
        width: 180px;
        background-size: cover;
        background-position: center;
        border-radius: 5px;
        box-shadow: 0 0 0 1px hsl(0deg 0% 0% / 20%);

        &.guest-avatar::after {
            outline: 9px solid hsl(0deg 0% 100%);
        }
    }

    .user_profile_edit_button {
        margin-left: 10px;
        width: 25px;
        text-align: center;
    }

    #user_profile_edit_button_icon {
        font-size: 18px;
    }

    #default-section {
        vertical-align: top;

        .default-field {
            margin-bottom: 10px;
        }
    }

    & hr {
        border: 1px solid hsl(0deg 0% 93%);
        margin: 5px 0;
    }

    #content {
        .field-section {
            margin-bottom: 10px;

            .name {
                color: hsl(0deg 0% 20%);
                font-weight: 600;
            }

            &[data-type="2"] .value {
                overflow-wrap: break-word;
            }
        }

        .rendered_markdown p {
            margin: 0;
        }
    }

    .col-left {
        padding: 0 10px 0 0;
        word-break: break-all;
    }

    .col-right {
        width: fit-content;
    }

    .tab-data {
        .active {
            display: block;
        }

        margin-bottom: 20px;
    }

    #user-profile-streams-tab {
        .stream_list_info {
            margin-bottom: 8px;
        }

        .stream-privacy {
            display: inline-block;
        }

        .filter-icon i {
            padding-right: 3px;
        }
    }

    .stream-list-top-section {
        display: flex;

        .stream-list-header {
            margin: 0;
            display: inline-block;
            font-weight: inherit;
        }

        .stream-search {
            margin-left: auto;
            align-self: center;
            padding-right: 20px;
            white-space: nowrap;
            text-overflow: ellipsis;
            overflow: hidden;
        }

        #clear_stream_search {
            display: none;
            padding: 5px 8px 5px 4px;
            position: relative;
            right: 0;
        }
    }

    .subscription-group-list,
    .subscription-stream-list {
        position: relative;
        border: 1px solid hsl(0deg 0% 83%);
        border-radius: 4px;
        overflow: auto;
        text-align: left;
        margin-bottom: 5px;
        -webkit-overflow-scrolling: touch;

        .remove-subscription-button {
            padding-top: 2px;
            padding-bottom: 2px;
        }

        .user-stream-list,
        .user-group-list {
            width: 100%;
            margin: auto;
            border-radius: 6px;

            & tr {
                border-bottom: 1px solid hsl(0deg 0% 87%);
                /* Ensure equal height for rows with a remove-subscription-button and
                   those without one. */
                height: 34px;

                &:last-of-type {
                    border-bottom: none;
                }

                & td {
                    padding: 4px 0;

                    &:first-of-type {
                        padding-left: 10px;
                    }

                    &:last-of-type {
                        padding-right: 10px;
                    }

                    &.remove_subscription {
                        text-align: right;
                    }
                }
            }

            & tbody:empty::after,
            &:empty::after {
                content: attr(data-empty);
                display: block;

                text-align: center;
                color: hsl(0deg 0% 67%);
            }

            &:empty {
                display: block;
                padding: 5px;
            }
        }
    }
}

@media (width < $md_min) {
    .message-info-popover,
    .user-info-popover {
        display: flex !important;
        justify-content: center;
        align-items: center;

        /* these are to override JS embedded inline styles. */
        top: 0 !important;
        left: 0 !important;
        margin: 0 !important;
        width: 100%;
        height: 100%;

        background-color: hsl(0deg 0% 0% / 70%);
        border-radius: 0;
        border: none;

        pointer-events: none;

        .popover-inner {
            background-color: hsl(0deg 0% 100%);
            pointer-events: all;
        }
    }

    .colorpicker-popover {
        display: flex !important;
        justify-content: center;
        align-items: center;

        /* these are to override JS embedded inline styles. */
        top: 0 !important;
        left: 0 !important;
        margin: 0 !important;
        width: 100%;
        height: 100%;

        background-color: hsl(0deg 0% 0% / 70%);
        border-radius: 0;
        border: none;

        pointer-events: none;

        .popover-inner {
            background-color: hsl(0deg 0% 100%);
            pointer-events: all;
        }

        @media (width < $sm_min) {
            .popover-inner {
                width: 70%;
            }

            .sp-picker-container {
                border-left: none !important;
            }
        }
    }

    .popover-flex {
        position: absolute;
        top: 0 !important;
        left: 0 !important;

        width: 100vw;
        height: 100vh;

        display: flex !important;
        justify-content: center;
        align-items: center;

        background-color: hsl(0deg 0% 0% / 70%);

        /* Needs to be higher than the 105 for div.overlay so that the
           emoji picker can render on top of the user status picker. */
        z-index: 106;

        opacity: 0;
        pointer-events: none;

        transition: all 0.3s ease;

        &.fade.in {
            opacity: 1;
            pointer-events: all;
        }

        .popover {
            display: inline-block;
        }
    }

    .emoji-info-popover {
        position: static;
        margin-right: 0;
    }

    #user-profile-modal {
        .stream-list-top-section {
            display: block;

            .header-section {
                width: 100%;
            }

            .stream-search {
                margin-bottom: 8px;
            }

            #clear_stream_search {
                padding-top: 1px;
            }
        }
    }
}

.popover.top .arrow::after {
    left: -1px;
}

#giphy_grid_in_popover {
    /* 300px of GIPHY grid + 5px is the extra gutter space
     * between gif columns. */
    width: 305px;
    border: 0;
    padding: 0;

    .giphy-gif {
        cursor: pointer;
    }

    .giphy-gif-img:focus {
        /* Red outline for clear visibility
         * of which image is in focus.
         */
        outline-color: hsl(0deg 100% 50%);
    }

    .search-box {
        display: flex;
        position: sticky;
        padding: 2px;

        & input {
            flex-grow: 1;
            margin: 5px;
            border-radius: 3px;
        }

        .clear_search_button {
            position: absolute;
            top: 5px;
            right: 3px;
            font-size: 16px;

            &:focus {
                .fa-remove {
                    outline: 2px solid hsl(215deg 47% 50%);
                }
            }
        }
    }

    .popover-content {
        overflow: auto;
        height: 200px;
        margin: 2px;
    }

    .popover-footer {
        text-align: center;
        background-color: hsl(0deg 0% 0%);
        border-radius: 0 0 6px 6px;

        & img {
            width: 120px;
        }
    }
}

@media (width < $md_min) {
    #giphy_grid_in_popover {
        position: static;
        top: 0 !important;
        left: 0 !important;
    }
}

.user_info_status_text {
    opacity: 0.8;

    .status-emoji {
        height: 18px;
        width: 18px;
        /* Override the default 3px left margin for status emoji, which is
           intended for their presentation elsewhere to the left of a
           user's name. */
        margin-left: 0;
        margin-right: 2px;
    }

    #status_message {
        padding: 1px 0;
        display: flex;
        align-items: baseline;
        hyphens: auto;
    }

    .status_text {
        overflow-wrap: anywhere;
    }
}

#move_topic_modal {
    & form {
        margin: 0;
    }

    /* Override the default border-radius to properly align
       the button corners with `stream_header_colorblock`. */
    .dropdown-toggle {
        border-radius: 1px 4px 4px 1px !important;
    }

    .dropdown-list-widget,
    .stream_header_colorblock,
    .inline_topic_edit {
        margin-bottom: 10px;
    }

    .topic_stream_edit_header {
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;

        #select_stream_id {
            border-left: 0;
            padding-left: 0;
            border-radius: 3px;
            margin: 0 5px 5px -10px;
            text-indent: 10px;
        }

        .dropdown-menu {
            position: fixed;
            top: 125px;
            left: 40px;
        }
    }
}

#language_selection_modal {
    width: min(750px, 70vw);
}

.default_language_modal_table {
    column-count: 3;

    @media (width < $md_min) {
        column-count: 2;
    }

    @media (width < $sm_min) {
        column-count: 1;
    }
}

~~~
#### app_components.css ####
~~~
/* Reusable, object-oriented CSS base components for the Zulip web app
   (not included in the portico CSS) */

.flex {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.hide {
    display: none;
}

kbd {
    display: inline-block;
    border: 1px solid hsl(0deg 0% 80%);
    border-radius: 4px;
    font-weight: 600;
    white-space: nowrap;
    background-color: hsl(0deg 0% 98%);
    color: hsl(0deg 0% 20%);
    margin: 0.25em 0.1em;
    padding: 0.1em 0.4em;
    text-shadow: 0 1px 0 hsl(0deg 0% 100%);
    /* Prevent selection */
    user-select: none;
}

@media (width < $sm_min) {
    .hide-sm {
        display: none !important;
    }

    .show-sm {
        display: block !important;
    }

    #settings_page .save-button-controls {
        display: block;
        margin: 10px 0 0;
    }
}

@media (width < $lg_min) {
    .hide-lg {
        display: none !important;
    }

    .show-lg {
        display: block !important;
    }
}

@media (width < $xl_min) {
    .hide-xl {
        display: none !important;
    }

    .show-xl {
        display: block !important;
    }
}

.light {
    font-weight: 300;
}

.inline-block {
    display: inline-block;
}

.display-block {
    display: block !important;
}

.box-shadow {
    box-shadow: 0 0 10px hsl(0deg 0% 0% / 10%);
}

.clear-float {
    clear: both;
}

.invisible {
    visibility: hidden;
}

.order-1 {
    order: 1;
}

.order-2 {
    order: 2;
}

.order-3 {
    order: 3;
}

/*
Consistent placeholder styling, introduced to allow us to style the
Reply box like a placeholder.  Chrome uses color to set placeholder,
while Firefox uses opacity, so we need to set both properties to avoid
mixed styling.

While we usually prefer opacity for text color in Zulip, there's some
evidence Edge may have bugs in its handling of placeholder opacity
CSS: https://github.com/necolas/normalize.css/issues/741
*/
.placeholder {
    color: hsl(0deg 0% 45%);
    opacity: 1;
}

textarea::placeholder,
input::placeholder {
    @extend .placeholder;
}

.new-style {
    /* -- base button styling -- */
    .button {
        padding: 7px 14px;
        margin: 0;
        min-width: 130px;

        font-weight: 400;
        line-height: normal;
        text-align: center;

        background-color: hsl(0deg 0% 100%);
        color: inherit;
        outline: none;
        border: 1px solid hsl(0deg 0% 80%);
        border-radius: 2px;

        box-shadow: none;

        cursor: pointer;
        transition: all 0.2s ease;

        /* -- button style variations -- */
        &.no-style {
            padding: 0;
            background-color: transparent;
            border: none;
            min-width: 0;
            width: auto;
            outline: none;
            box-shadow: none !important;
        }

        &.rounded {
            border-radius: 4px;
        }

        &.green {
            background-color: hsl(150deg 31% 53%);
        }

        &.grey {
            background-color: hsl(0deg 0% 67%);
        }

        &.small {
            font-size: 0.8rem;
            min-width: inherit;
            padding: 6px 10px;
        }

        &:hover,
        &:focus {
            border-color: hsl(0deg 0% 60%);
        }

        &:active {
            border-color: hsl(0deg 0% 60%);
            color: inherit;
            background-color: hsl(0deg 0% 95%);
        }

        &.sea-green {
            color: hsl(156deg 41% 40%);
            border-color: hsl(156deg 28% 70%);

            &:hover,
            &:focus {
                border-color: hsl(156deg 30% 50%);
            }

            &:active {
                border-color: hsl(156deg 30% 40%);
                color: hsl(156deg 44% 43%);
                background-color: hsl(154deg 33% 96%);
            }
        }

        &.btn-warning {
            color: hsl(35deg 70% 56%);
            border-color: hsl(35deg 98% 84%);

            &:hover,
            &:focus {
                border-color: hsl(35deg 55% 70%);
            }

            &:active {
                color: hsl(35deg 82% 40%);
                border-color: hsl(35deg 55% 70%);
                background-color: hsl(33deg 48% 96%);
            }
        }

        &.btn-danger {
            color: hsl(357deg 64% 72%);
            border-color: hsl(4deg 56% 82%);

            &:hover,
            &:focus {
                border-color: hsl(2deg 46% 68%);
            }

            &:active {
                color: hsl(357deg 55% 63%);
                border-color: hsl(2deg 46% 68%);
                background-color: hsl(7deg 82% 98%);
            }
        }

        &.btn-link {
            color: hsl(208deg 56% 53%);
            text-decoration: none;

            &:hover,
            &:focus {
                color: hsl(208deg 56% 38%);
            }
        }

        &:disabled {
            cursor: not-allowed;
            filter: saturate(0);
            background-color: hsl(0deg 0% 93%);
            color: hsl(0deg 3% 52%);

            &:hover {
                background-color: hsl(0deg 0% 93%);
                color: hsl(156deg 39% 54%);
                border-color: hsl(156deg 39% 77%);
            }
        }
    }

    /* -- tab switcher -- */

    .tab-switcher {
        font-weight: initial;
        margin: 2px 4px;
        display: inline-block;

        .ind-tab {
            display: inline-block;
            width: 90px;
            margin: 0 -0.5px;
            text-align: center;
            text-overflow: ellipsis;
            white-space: nowrap;
            overflow: hidden;
            vertical-align: bottom; /* See https://stackoverflow.com/a/43266155/ */
            padding: 3px 10px;
            background-color: hsl(0deg 0% 100%);
            cursor: pointer;
            justify-content: center;
            align-items: center;

            &:focus {
                outline: none;
            }

            &:not(.selected) {
                border: 1px solid hsl(0deg 0% 80%);
            }

            &.first {
                border-radius: 5px 0 0 5px;
                border-right: 1px solid transparent;
            }

            &.middle {
                border-right: 1px solid transparent;
            }

            &.last {
                border-radius: 0 5px 5px 0;
            }

            &.selected {
                position: relative;
                background-color: hsl(0deg 0% 53%);
                color: hsl(0deg 0% 100%);
                border: 1px solid hsl(0deg 0% 47%);
                z-index: 2;
            }

            &.disabled {
                pointer-events: none;
                color: hsl(0deg 0% 80%);
                border-color: hsl(0deg 0% 87%);
            }
        }

        &.large .ind-tab {
            width: 100%;
        }

        &.allow-overflow {
            display: flex;

            .ind-tab {
                display: flex;
                text-overflow: initial;
                white-space: initial;
                vertical-align: middle;
            }
        }
    }

    .stream_sorter_toggle {
        margin-left: auto;
    }
}

/* -- unified overlay design component -- */
div.overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    -webkit-overflow-scrolling: touch;

    background-color: hsl(0deg 0% 13% / 80%);
    z-index: 105;

    pointer-events: none;
    opacity: 0;
    visibility: hidden;

    transition: all 0.2s ease-in;
    overflow: hidden;

    .overlay-content {
        transform: translateY(20px);
        transition: transform 0.2s ease-in;
        z-index: 102;
    }

    &.show {
        opacity: 1;
        pointer-events: all;
        visibility: visible;
        transition: opacity 0.2s ease-out;

        .overlay-content {
            transform: translateY(0);
            transition-timing-function: ease-out;
        }
    }
}

.input-append {
    font-size: 90%;
    letter-spacing: -0.3em;
    display: block;
}

.input-append input[type="text"],
.new-style input[type="text"] {
    border-radius: 5px;
    box-shadow: none;
    margin: 0;
}

.clear_search_button {
    &:hover {
        color: hsl(0deg 0% 0%);
    }

    &:disabled {
        visibility: hidden;
    }

    &,
    &:focus,
    &:active,
    &:disabled:hover {
        position: relative;
        right: 20px;
        background: none;
        border: none;
        text-align: center;
        padding-top: 8px;
        padding-left: 4px;
        color: hsl(0deg 0% 80%);
        text-shadow: none;
        outline: none !important;
        box-shadow: none;
        z-index: 5;

        #set-user-status-modal & {
            margin-left: -26px;
            right: 0;
            padding-top: 6px;
        }
    }
}

.grey-box {
    margin: 0;
    padding: 5px 10px;
    background-color: hsl(0deg 0% 98%);
    border: 1px solid hsl(0deg 0% 87%);
    border-radius: 4px;

    list-style-type: none;
}

.white-box {
    background-color: hsl(0deg 0% 100%);
    border: 1px solid hsl(0deg 0% 87%);
}

.guest-avatar {
    position: relative;
    overflow: hidden;

    &::after {
        content: " ";
        background-color: hsl(0deg 0% 47%);
        position: absolute;
        bottom: -30%;
        right: -30%;
        width: 50%;
        height: 50%;
        transform: rotate(45deg);
    }
}

.dependent-settings-block {
    margin: 15px 0 -5px 23px;
}

@media (width < $md_min) {
    /* Override Bootstrap's responsive grid to display input at full width */
    .input-append .stream-list-filter {
        /* Input width = 100% - 10px margin x2 - 6px padding x2 - 1px border x2. */
        width: calc(100% - 34px);
        margin-left: 10px;
    }

    .input-append .topic-list-filter {
        /* Input width = 100% - 11px margin x2 - 6px padding x2 - 1px border x2. */
        width: calc(100% - 36px);
        margin-left: 11px;
        margin-bottom: 5px;
    }
}

.topic-list-filter {
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;

    & input {
        padding-right: 20px;
    }
}

.stream-selection-header-colorblock {
    /* box-shadow: 0px 2px 3px hsl(0, 0%, 80%); */
    box-shadow: inset 0 2px 1px -2px hsl(0deg 0% 20%),
        inset 2px 0 1px -2px hsl(0deg 0% 20%),
        inset 0 -2px 1px -2px hsl(0deg 0% 20%);
    width: 10px;
    border-radius: 3px 0 0 3px;
    border-bottom: 0;
}

.stream_header_colorblock {
    @extend .stream-selection-header-colorblock;
    margin-bottom: 5px;
    z-index: 1;
}

.edit-controls .fa-angle-right,
.topic_stream_edit_header .fa-angle-right {
    font-size: 0.9em;
    -webkit-text-stroke: 0.05em;
    position: relative;
    margin: 0 5px;
    top: 9px;
}

/* Standard loading indicators generated by the loading.ts API */
.loading_indicator_spinner {
    /* If you change these, make sure to adjust the constants in
       loading.make_indicator as well */
    height: 38px;
    width: 38px;
    float: left;
}

.loading_indicator_text {
    /* If you change these, make sure to adjust the constants in
       loading.make_indicator as well */
    margin-left: 5px;
    font-size: 1.2em;
    font-weight: 300;
    line-height: 38px;
}

.upgrade-tip,
.upgrade-or-sponsorship-tip {
    width: fit-content;

    &::before {
        content: "\f135";
        margin-right: 6px;
    }
}

.upgrade-tip:hover {
    color: hsl(0deg 0% 20%);
    border: 1px solid hsl(49deg 20% 60%);
    box-shadow: 0 0 4px hsl(199deg 79% 56% / 20%);

    text-decoration: none;
}

.upgrade-tip,
.upgrade-or-sponsorship-tip,
.tip {
    position: relative;
    display: block;
    background-color: hsl(46deg 63% 95%);
    border: 1px solid hsl(49deg 20% 84%);
    border-radius: 4px;
    padding: 10px;
    margin: 10px 0;
    font-size: 1rem;
    line-height: 1.5;
    color: hsl(0deg 0% 40%);

    &::before {
        display: inline;

        font-family: FontAwesome;
        font-weight: 600;
    }
}

.tip::before {
    content: "\f0a2";
    margin-right: 8px;
}

/* We are mostly consistent in how we style
   unread counts, except for starred messages.
   This is the common section.
*/
.unread_count {
    float: right;
    padding: 0 4px;
    height: 16px;
    line-height: 16px;
    font-size: 12px;
    font-weight: normal;
    letter-spacing: 0.6px;
    border-radius: 4px;
    background-color: hsl(105deg 2% 50%);
    color: hsl(0deg 0% 100%);
}

.unread_mention_info:not(:empty) {
    margin-right: 5px;
    margin-left: 2px;
    opacity: 0.7;
}

/* Implement the web app's default-hidden convention for alert
   elements.  Portico pages lack this CSS and thus show them by
   default. */
.alert {
    display: none;

    &.show {
        display: block;
    }

    &#organization-status {
        margin: 20px;
    }

    &.stream_create_info {
        margin: 10px 10px 0;
    }

    .bankruptcy_unread_count {
        font-weight: 600;
    }
}

.white_zulip_icon_without_text {
    display: inline-block;
    background-image: url("../images/logo/white-zulip-logo-without-text.svg");
    background-size: cover;
}

.only-visible-for-spectators {
    display: none;
}

.spectator-view {
    /* Add this class to elements which a
     * spectator cannot use. */
    .hidden-for-spectators {
        display: none !important;
    }

    .only-visible-for-spectators {
        display: revert;
    }
}

.animated-purple-button {
    color: hsl(0deg 0% 100%);
    transition: all 80ms linear;
    box-shadow: none;
    /* This color just passes WCAG AA */
    background-color: hsl(240deg 96% 68%);
    cursor: pointer;
    border: none;
    border-radius: 4px;
    text-align: center;
    white-space: nowrap;

    &:hover {
        /* This color passes WCAG AAA */
        background-color: hsl(240deg 41% 50%);
        box-shadow: 0 1px 4px hsl(0deg 0% 0% / 30%);
    }

    &:focus {
        background-color: hsl(240deg 41% 50%);
        box-shadow: 0 1px 4px 0 hsl(235deg 18% 7%);
        outline: none;
    }
}

.color_animated_button {
    display: flex;
    justify-content: center;
    background-color: hsl(0deg 0% 90%);
    color: hsl(0deg 0% 0%);
    border-radius: 4px;

    & span {
        color: hsl(0deg 0% 0%);
    }

    &:hover {
        cursor: pointer;
        background-color: hsl(240deg 96% 68%);
        color: hsl(0deg 0% 100%);

        & span {
            color: hsl(0deg 0% 100%);
            transition: all 0.2s ease;
        }

        transition: all 0.2s ease;
    }

    * {
        padding: 6px 3px;
    }

    .fa {
        position: relative;
        top: 3px;
    }
}

.table-striped {
    table-layout: auto;
    border-collapse: separate;

    & thead th {
        color: inherit;
        background-color: hsl(0deg 0% 100%);
        border-top: 1px solid hsl(0deg 0% 0% / 20%) !important;
        border-bottom: 1px solid hsl(0deg 0% 0% / 20%) !important;

        &.active::after,
        &[data-sort]:hover::after {
            content: " \f0d8";
            white-space: pre;
            display: inline-block;
            position: relative;
            padding-top: 3px;
            font: normal normal normal 12px/1 FontAwesome;
            font-size: inherit;
        }

        &.active {
            opacity: 1;
            transition: opacity 100ms ease-out;

            &.descend::after {
                content: " \f0d7";
            }
        }

        &[data-sort]:hover {
            cursor: pointer;
            background-color: hsl(0deg 0% 95%) !important;
            transition: background-color 100ms ease-in-out;

            &:not(.active)::after {
                opacity: 0.3;
            }
        }
    }

    /* Force the actions column to use the minimum space necessary */
    .actions {
        width: 1%;
        white-space: nowrap;
    }
}

#stream_settings .save-button-controls,
#settings_page .save-button-controls {
    display: inline;
    margin-left: 15px;

    &.hide {
        display: none;
    }

    .save-discard-widget-button {
        border-radius: 5px;
        border: 1px solid hsl(0deg 0% 80%);
        padding: 3px 14px 4px 11px;
        text-decoration: none;
        color: hsl(0deg 0% 47%);
        min-width: 80px;
        /* Limit the height of the button */
        line-height: 1.2;
        vertical-align: text-bottom;

        &:hover,
        &:focus {
            border: 1px solid hsl(0deg 0% 61%);

            .discard-button.save-discard-widget-button-text {
                color: hsl(0deg 0% 18%);
            }
        }

        &.primary {
            background-color: hsl(156deg 30% 50%);
            color: hsl(0deg 0% 100%);
            border: 1px solid hsl(155deg 30% 50%);

            &:hover,
            &:focus {
                background-color: hsl(166deg 35% 57%);
                border: 1px solid hsl(166deg 35% 57%);
            }

            .save-discard-widget-button-icon {
                font-weight: lighter;
                color: hsl(0deg 0% 100%);
            }

            &.saving {
                background-color: hsl(156deg 14% 40%);
                border-color: hsl(156deg 14% 40%);
            }
        }

        &.save-button {
            margin-right: 5px;

            .save-discard-widget-button-loading {
                display: none;
            }

            &.saving {
                .save-discard-widget-button-icon {
                    display: none;
                }

                .save-discard-widget-button-loading {
                    display: inline-block;
                    margin-right: 2px;
                }
            }
        }

        .save-discard-widget-button-icon {
            vertical-align: middle;
            margin-right: 3px;
            font-size: 15px;
            font-weight: 500;
        }

        .save-discard-widget-button-text {
            vertical-align: middle;
            line-height: 1;
        }
    }
}

.stream-privacy-type-icon {
    &.zulip-icon-globe {
        position: relative;
        top: 1px;
        padding-right: 1px;
        font-size: 0.75em;
    }

    &.fa-lock {
        padding-right: 1px;
        font-size: 0.865em;
    }

    &.hashtag:empty::after {
        font-size: 1em;
    }
}

#settings_content,
#stream_settings,
#stream-creation,
#edit_bot_modal {
    .dropdown-list-widget .dropdown-list-wrapper {
        width: fit-content;

        & span {
            min-width: 210px;
            width: fit-content;
        }
    }
}

~~~
#### image_upload_widget.css ####
~~~
/* common CSS for all image upload widget's */
.image_upload_widget {
    position: relative;
    border-radius: 5px;
    box-shadow: 0 0 10px hsl(0deg 0% 0% / 10%);
    overflow: hidden;

    transition: all 0.3s ease;

    .image-block {
        background-size: contain;
        height: 100%;
    }

    .image-hover-background {
        content: "";
        background-color: hsl(0deg 0% 0% / 60%);
        height: 100%;
        width: 100%;
        z-index: 99;
        position: absolute;
        display: none;
        cursor: pointer;
    }

    .image_upload_button {
        position: absolute;
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        text-align: center;
        justify-content: center;
        box-shadow: 0 0 10px hsl(0deg 0% 0% / 10%);
        z-index: 99;
    }

    .image-delete-button {
        background: none;
        border: none;
        cursor: pointer;
        color: hsl(0deg 0% 75%);
        opacity: 0;
        padding: 0;
        position: absolute;
        font-size: 2rem;
        top: 10px;
        right: 10px;
        z-index: 99;
        line-height: 20px;
    }

    .image-disabled-text {
        color: hsl(0deg 0% 100%);
        cursor: not-allowed;
        position: absolute;
        text-align: center;
        visibility: hidden;
        z-index: 99;
    }

    .image-delete-text,
    .image-upload-text,
    .image-disabled-text {
        box-sizing: border-box;
        width: 100%;
        padding: 0 10px;
    }

    .image-delete-button:focus,
    .image-delete-button:hover {
        color: hsl(0deg 0% 100%);
    }

    .image-delete-button:hover ~ .image-upload-text {
        visibility: hidden;
    }

    .image-delete-button:hover ~ .image-delete-text {
        visibility: visible;
    }

    .image-delete-text {
        color: hsl(0deg 0% 100%);
        font-size: 0.85rem;
        position: absolute;
        visibility: hidden;
        z-index: 99;
    }

    .image-upload-text {
        cursor: pointer;
        font-size: 0.85rem;
        color: hsl(0deg 0% 85%);
        position: absolute;
        z-index: 99;
        visibility: hidden;
    }

    .image-upload-text:hover {
        color: hsl(0deg 0% 100%);
    }

    .upload-spinner-background {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: hsl(0deg 0% 10%);
        font-size: 0.8rem;
        width: 100%;
        opacity: 0.8;
        height: 100%;
        position: absolute;
        visibility: hidden;
        z-index: 99;
        cursor: pointer;
        border-radius: 5px;
    }

    .hide {
        display: none;
    }

    &:hover {
        .image-upload-text {
            visibility: visible;
        }

        .image-delete-button {
            opacity: 1;
        }

        .image-disabled-text {
            visibility: visible;
        }

        .image-hover-background {
            display: block;
        }
    }
}

.user-avatar-section,
.realm-logo-section,
.realm-icon-section {
    margin: 20px 0;
}

/* CSS related to settings page user avatar upload widget only */
#user-avatar-upload-widget {
    .image-block {
        width: 200px;
        height: 200px;
    }
}

#user-avatar-source {
    font-size: 1em;
    z-index: 99;
    margin-top: 10px;
}

/* CSS related to settings page realm icon upload widget only */
#realm-icon-upload-widget {
    width: 100px;
    height: 100px;
    box-shadow: 0 0 10px hsl(0deg 0% 0% / 10%);

    .image-delete-button {
        top: 5px;
        right: 5px;
    }
}

/* CSS related to settings page realm day/night logo upload widget only */
#realm-day-logo-upload-widget,
#realm-night-logo-upload-widget {
    width: 220px;
    height: 55px;
    text-align: center;

    .image-delete-button {
        top: 5px;
        right: 5px;
    }
}

#realm-day-logo-upload-widget {
    background-color: hsl(0deg 100% 100%);
}

#realm-night-logo-upload-widget {
    background-color: hsl(212deg 28% 18%);
}

.realm-logo-block {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 0 20px;
}

.realm-logo-group {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}

/* CSS  related to upload widget's preview image */
.upload_widget_image_preview {
    object-fit: cover;
}

~~~
#### alerts.css ####
~~~
$alert-red: hsl(16deg 60% 45%);
$alert-error-red: hsl(0deg 80% 40%);

.alert-display {
    display: none;

    &.show {
        display: block;
    }
}

.alert-animations {
    &.show {
        animation-name: fadeIn;
        animation-duration: 0.3s;
        animation-fill-mode: forwards;
    }

    &.fade-out {
        animation-name: fadeOut;
        animation-duration: 0.3s;
        animation-fill-mode: forwards;
    }

    .faded {
        opacity: 0.7;
    }
}

/* alert box component changes */
.alert-box {
    position: absolute;
    top: 0;
    left: 0;
    width: 900px;
    margin-left: calc(50% - 450px);
    z-index: 220;
    max-height: 100%;
    overflow-y: auto;
    overscroll-behavior: contain;

    .stacktrace {
        @extend .alert-display, .alert-animations;

        font-size: 1rem;
        color: hsl(0deg 80% 40%);

        margin-top: 5px;
        padding: 1rem 0;

        background-color: hsl(0deg 100% 98%);
        border-radius: 4px;
        border: 1px solid hsl(0deg 80% 40%);
        box-shadow: 0 0 2px hsl(0deg 80% 40%);

        .stacktrace-header {
            display: flex;
            justify-content: space-between;

            .message {
                flex: 1 1 auto;
            }

            .warning-symbol,
            .exit {
                flex: 0 0 auto;
                font-size: 1.3rem;
                padding: 0 1rem;
            }

            .exit::after {
                cursor: pointer;
                font-size: 2.3rem;
                content: "\d7";
            }
        }

        .stacktrace-content {
            font-family: "Source Code Pro", monospace;
            font-size: 0.85rem;

            margin-top: 1rem;

            .stackframe {
                padding-left: calc(3.3rem - 14px);
                padding-right: 1rem;
            }
        }

        .expand {
            cursor: pointer;
            color: hsl(0deg 32% 83%);

            &:hover {
                color: hsl(0deg 0% 20%);
            }
        }

        .subtle {
            color: hsl(0deg 7% 45%);
        }

        .code-context {
            color: hsl(0deg 7% 15%);
            background-color: hsl(0deg 7% 98%);
            box-shadow: inset 0 11px 10px -10px hsl(0deg 7% 70%),
                inset 0 -11px 10px -10px hsl(0deg 7% 70%);

            margin-top: 1em;
            margin-bottom: 1em;

            .code-context-content {
                padding: 1rem 0;
                white-space: pre;
                overflow-x: auto;
            }

            .line-number {
                width: 3rem;
                display: inline-block;
                text-align: right;
                color: hsl(0deg 7% 35%);
            }

            .focus-line {
                background-color: hsl(0deg 7% 90%);
                width: 100%;
            }
        }
    }

    .alert {
        @extend .alert-animations;

        font-size: 1rem;
        border-radius: 4px;
        background-color: hsl(0deg 0% 100%);

        position: relative;

        /* gives room for the error icon and the exit button. */
        padding: 10px 50px;

        text-shadow: none;

        color: $alert-red;
        border: 1px solid $alert-red;
        box-shadow: 0 0 2px $alert-red;

        &::before {
            float: left;
            margin-left: -38px;

            font-family: FontAwesome;
            font-size: 1.3em;
            line-height: 1;
            overflow: hidden;
            content: "\f071";

            color: hsl(16deg 60% 55%);
        }

        &::after {
            clear: both;
            content: "";
            display: table;
        }

        &.alert-error {
            color: $alert-error-red;
            border: 1px solid $alert-error-red;
            box-shadow: 0 0 2px $alert-error-red;

            &::before {
                color: $alert-error-red;
            }
        }

        .exit {
            float: right;
            margin: -10px -50px -10px 0;
            padding: 10px;

            font-size: 2.5em;
            font-weight: 300;
            line-height: 1ex;
            overflow: hidden;

            cursor: pointer;

            &::after {
                content: "\d7";
            }
        }
    }
}

/* animation section */
@keyframes fadeIn {
    0% {
        display: block;
        opacity: 0;
        transform: translateY(-100px);
    }

    100% {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes fadeOut {
    0% {
        opacity: 1;
        transform: translateY(0);
    }

    100% {
        display: none;
        opacity: 0;
        transform: translateY(-100px);
    }
}

/* @media queries */
@media (width < $lg_min) {
    .alert-box {
        width: 80%;
        left: 10%;
        margin-left: 0;
    }
}

#request-progress-status-banner {
    display: none;
    align-items: center;
    padding: 5px 10px;
    margin-top: 10px;
    grid-template-columns: 80px auto 50px;

    &.show {
        display: grid !important;
    }

    &.alert-loading {
        .alert-zulip-logo,
        .loading-indicator {
            display: block;
        }

        /* Hide exit button since clicking it will be useless in
           this scenario. */
        .exit {
            display: none;
        }
    }

    &.alert-success .success-indicator {
        display: block;
    }

    &.alert-loading,
    &.alert-success {
        border-color: hsl(156deg 28% 70%);
        box-shadow: 0 0 2px hsl(156deg 28% 70%);

        .exit {
            color: hsl(156deg 30% 50%);
        }
    }

    &::before {
        content: "";
        margin-left: 0;
    }

    .alert-zulip-logo {
        display: none;
        margin: auto;
        grid-column: 1 / 2;
        grid-row-start: 1;
    }

    .loading-indicator {
        display: none;
        margin: auto;
        grid-column: 1 / 2;
        grid-row-start: 1;
    }

    .success-indicator {
        display: none;
        margin: auto;
        grid-column: 1 / 2;
        grid-row-start: 1;
        padding: 7px;
        font-size: 1.5em;
        line-height: 0;
        color: hsl(156deg 30% 50%);
    }

    .alert-content {
        grid-column: 2 / 3;
        grid-row-start: 1;
        color: hsl(0deg 0% 20%);
    }

    .exit {
        float: unset;
        margin: 0;
        margin-left: auto;
        grid-column: 3 / 4;
        grid-row-start: 1;
        line-height: 0;
    }
}

~~~
#### footer.css ####
~~~
:root {
    --color-footer-background: hsl(238deg 28% 27%);
    --color-links: hsl(238deg 100% 82%);

    @media (prefers-color-scheme: dark) {
        --color-footer-background: hsl(238deg 28% 21%);
    }
}

#footer {
    background: var(--color-footer-background);
    box-sizing: border-box;

    & ul {
        /* Override bootstrap defaults */
        list-style: none;
        margin: 0;
    }

    .footer__container {
        max-width: 1132px;
        padding: 52px 52px 0;
        display: flex;
        justify-content: space-between;
        gap: 40px;
        flex-flow: row wrap;
        margin: 0 auto;
    }

    .footer__section {
        flex-shrink: 0;
    }

    .footer__section-title {
        display: block;
        font-style: normal;
        font-weight: 700;
        font-size: 18px;
        line-height: 133%;
        letter-spacing: 0.1em;
        color: hsl(0deg 0% 100%);
        opacity: 0.8;
        text-transform: uppercase;
        border-bottom: 0;
        margin-bottom: 0;
    }

    .footer__section ul {
        margin: 28px 0 0;
        display: flex;
        flex-direction: column;
        align-items: flex-start;

        & li {
            margin-bottom: 10px;
        }
    }

    & li {
        font-style: normal;
        font-weight: 400;
        font-size: 16px;
        line-height: 20px;
        color: var(--color-links);
        border-bottom: 1px solid var(--color-footer-background);
        transition: border 0.4s ease-out;
    }

    & a,
    a:visited {
        font-weight: 400;
        font-size: 16px;
        color: var(--color-links);
    }

    & a:hover,
    a:focus {
        color: var(--color-links);
        border-bottom: 1px solid var(--color-links);
        transition: none;
        text-decoration: none;
        outline: none;
    }

    .footer__legal {
        margin: 24px 0 5px;
        padding: 0 52px;
        border-top: 1px solid hsl(0deg 0% 100% / 10%);

        & a {
            margin-bottom: 10px;
            border-bottom: 1px solid var(--color-footer-background);

            &:hover {
                border-bottom: 1px solid var(--color-links);
            }
        }

        &.footer__legal_not_corporate {
            margin-top: 0;
        }
    }

    .footer__legal-container {
        max-width: 1132px;
        padding-top: 15px;
        display: flex;
        justify-content: space-between;
        flex-flow: row wrap;
        margin: 0 auto;

        box-sizing: border-box;
        font-style: normal;
        font-weight: 400;
        font-size: 14px;
        line-height: 18px;
    }

    .footer__legal-spacer {
        flex-grow: 1;
    }

    .footer__legal-container .copyright {
        color: hsl(0deg 0% 100% / 50%);
        margin-bottom: 8px;
    }

    .footer__legal-container a {
        font-size: 14px;
        line-height: 18px;
    }

    .footer__legal-container a:not(:last-child) {
        margin-right: 2em;
    }

    .footer__section .extra_margin {
        margin-bottom: 40px;
    }

    /* #footer responsivity and global fixes */
    @media (max-width: 940px) {
        .footer__container {
            justify-content: flex-start;
            row-gap: 0;
        }

        .footer__legal-container {
            justify-content: flex-end;
        }
    }

    @media (max-width: 600px) {
        .footer__legal {
            padding: 0 10px;
        }

        .footer__legal-spacer {
            width: 100%;
        }

        .footer__legal-container {
            column-gap: 20px;
            justify-content: center;

            & a:not(:last-child) {
                margin-right: 0;
            }
        }
    }

    @media (max-width: 400px) {
        .footer__container {
            gap: 0;
            flex-direction: column;
        }

        .footer__section .extra_margin {
            margin-bottom: 36px;
        }
    }
}

~~~
#### input_pill.css ####
~~~
.pill-container {
    display: inline-flex;
    flex-wrap: wrap;

    padding: 2px;
    border: 1px solid hsl(0deg 0% 0% / 15%);
    border-radius: 4px;
    align-items: center;

    cursor: text;

    .pill {
        display: inline-flex;
        align-items: center;

        height: 20px;
        margin: 1px 2px;

        color: inherit;
        border: 1px solid hsl(0deg 0% 0% / 15%);

        border-radius: 4px;
        background-color: hsl(0deg 0% 0% / 7%);
        cursor: pointer;

        &:focus {
            color: hsl(0deg 0% 100%);
            border: 1px solid hsl(176deg 78% 28%);
            background-color: hsl(176deg 49% 42%);
            outline: none;
        }

        .pill-image {
            height: 20px;
            width: 20px;
            border-radius: 4px 0 0 4px;
        }

        .pill-value {
            margin: 0 5px;
        }

        .exit {
            opacity: 0.5;
            font-size: 1.3em;
            margin-right: 3px;
        }

        &:hover .exit {
            opacity: 1;
        }
    }

    &.not-editable {
        cursor: not-allowed;
        border: none;
        background-color: transparent;
        padding: 0;

        .pill {
            padding-right: 4px;
            cursor: not-allowed;

            &:focus {
                color: inherit;
                border: 1px solid hsl(0deg 0% 0% / 15%);
                background-color: hsl(0deg 0% 0% / 7%);
            }

            .exit {
                display: none;
            }
        }
    }

    &.pill-container-btn {
        cursor: pointer;
        padding: 0;

        .pill {
            margin: 0;
            border: none;

            .exit {
                display: none;
            }
        }
    }

    .input {
        display: inline-block;
        padding: 2px 4px;

        min-width: 2px;
        word-break: break-all;

        outline: none;

        &.shake {
            animation: shake 0.3s cubic-bezier(0.36, 0.07, 0.19, 0.97) both;
            transform: translate3d(0, 0, 0);
            backface-visibility: hidden;
            perspective: 1000px;
        }
    }
}

.pm_recipient .pill-container {
    padding: 0 2px;
    flex-grow: 1;
    align-content: center;
    border: 1px solid hsl(0deg 0% 0% / 20%);

    .input {
        height: 20px;

        &:first-child:empty::before {
            content: attr(data-no-recipients-text);
            opacity: 0.5;
        }
    }

    .pill + .input:empty::before {
        content: attr(data-some-recipients-text);
        opacity: 0.5;
    }
}

.deactivated-pill {
    background-color: hsl(0deg 86% 86%) !important;
}

.add_subscribers_container .pill-container {
    width: 100%;
    background-color: hsl(0deg 0% 100%);

    .input:first-child:empty::before {
        opacity: 0.5;
        content: attr(data-placeholder);
    }
}

@keyframes shake {
    10%,
    90% {
        transform: translate3d(-1px, 0, 0);
    }

    20%,
    80% {
        transform: translate3d(2px, 0, 0);
    }

    30%,
    50%,
    70% {
        transform: translate3d(-3px, 0, 0);
    }

    40%,
    60% {
        transform: translate3d(3px, 0, 0);
    }
}

~~~
#### markdown.css ####
~~~
.markdown {
    font-weight: 400;
    font-size: 1rem;
    line-height: 1.5;
    overflow: auto;

    & h1[id],
    h2[id],
    h3[id],
    h4[id] {
        &::before {
            display: block;
            content: " ";
            visibility: hidden;
        }
    }

    & h2[id],
    h3[id],
    h4[id] {
        &::before {
            margin-top: -10px;
            height: 10px;
        }
    }

    & h1 {
        border-bottom: 1px solid hsl(0deg 0% 93%);
        padding-bottom: 10px;
        margin-bottom: 15px;

        &[id] {
            &::before {
                margin-top: -30px;
                height: 30px;
            }
        }

        &#zulip-administration {
            font-size: 1.75em;
            padding: 10px 0;
            margin-bottom: 0;
            line-height: 100%;
        }
    }

    & h2 {
        font-size: 1.5em;
        line-height: 1.25;
        margin: 20px 0 5px;
    }

    & h3 {
        font-size: 1.25em;
        line-height: 1.25;
        opacity: 1;
        margin: 20px 0 5px;
    }

    & h1,
    h2,
    h3 {
        font-weight: 700;
        user-select: none;

        &:hover {
            cursor: pointer;

            &::after {
                display: inline-block;
                font: normal normal normal 16px/1 FontAwesome;

                cursor: pointer;
                content: "\f0c1";
                margin-left: 5px;
                vertical-align: middle;
            }
        }
    }

    & h5,
    h6 {
        margin: 10px 0;
        line-height: 20px;
    }

    /* Since markdown doesn't make it easy to put an HTML element around a
       markdown table, we instead have a model of putting an empty div
       before it to configure a specific table's styling. */
    & div.centered_table + table td:not(:first-child),
    div.centered_table + table th {
        text-align: center;
    }

    .legend_symbol {
        position: absolute;
        left: calc(40px);
        transform: translateX(-50%);

        /* Adjust for 50px closed left sidebar state */
        @media (width <= 800px) {
            left: calc(5% + 50px);
        }
    }

    .legend_label {
        position: relative;
        left: calc(30px);
    }

    & li {
        line-height: 150%;
    }

    & ol {
        counter-reset: item;
        list-style: none;

        & > li {
            position: relative;
            vertical-align: top;
            /* This needs to be wide enough for 2-digit numbers. */
            padding-left: 33px;
            top: -2px;
            counter-increment: item;

            &::before {
                position: absolute;
                top: 0;
                left: 0;
                content: counter(item);
                display: inline-block;
                vertical-align: top;
                padding: 3px 6.5px 3px 7.5px;
                margin-right: 5px;
                background-color: hsl(170deg 48% 54%);
                color: hsl(0deg 0% 100%);
                border-radius: 100%;
                font-size: 0.9em;
                line-height: 1.1;
                text-align: center;
            }

            .codehilite {
                background-color: hsl(0deg 0% 100%);

                & pre {
                    white-space: pre;
                    overflow-x: auto;
                }
            }

            & > ul {
                margin-bottom: 5px;
            }

            .warn,
            .tip,
            .keyboard_tip {
                margin: 5px 25px;
            }
        }

        @media (width <= 500px) {
            margin-left: 0;
        }
    }

    & ul {
        margin: 0 10px 15px 25px;

        /* Avoid extra whitespace after nested bulleted lists. */
        & ul {
            margin: 0 20px;
        }

        & > li {
            margin: 5px 0 10px;

            & > p {
                margin: 0 0 5px;
            }

            & > p:first-child {
                margin: 0;
            }
        }
    }

    .content {
        padding: 30px;
        max-width: 700px;
        background-color: hsl(0deg 0% 100%);

        & ol li p:not(:first-child) {
            display: block;
        }

        & > ol {
            margin: 15px 10px;

            & > li {
                margin: 2.5px 0;
            }
        }

        & i.zulip-icon {
            margin: 0 2px 2px;
            vertical-align: middle;
        }

        @media (width <= 500px) {
            padding: 10px;
        }
    }

    & a {
        color: hsl(176deg 46% 41%);
        font-weight: 600;

        & code {
            color: hsl(176deg 46% 41%);
        }
    }

    & strong {
        font-weight: 600;
    }

    & img {
        vertical-align: top;
        box-shadow: 0 0 4px hsl(0deg 0% 0% / 5%);
        border: 1px solid hsl(0deg 0% 87%);
        border-radius: 4px;

        &.inline {
            height: 1.4em;
            box-shadow: none;
        }

        &.emoji-small {
            width: 20px;
            box-shadow: none;
            border: none;
            vertical-align: sub;
        }

        &.emoji-big {
            width: 25px;
            box-shadow: none;
            border: none;
        }

        &.mobile-icon {
            width: 24px;
            box-shadow: none;
            border: none;
        }
    }

    .warn,
    .tip,
    .keyboard_tip {
        position: relative;
        display: block;
        background-color: hsl(210deg 22% 96%);
        border: 1px solid hsl(210deg 22% 90%);
        border-radius: 4px;
        padding: 10px;
        margin: 5px 0;

        & p {
            margin-bottom: 0;
        }

        & p:first-of-type {
            display: inline;
        }
    }

    .tip,
    .keyboard_tip {
        background-color: hsl(46deg 63% 95%);
        border: 1px solid hsl(46deg 63% 84%);
    }

    .tip::before {
        display: inline;
        content: "\f0eb   Tip:  ";
        font-family: FontAwesome, "Source Sans 3", sans-serif;
        font-weight: 600;
    }

    .keyboard_tip::before {
        display: inline;
        content: "\f11c   Keyboard shortcut:  ";
        font-family: FontAwesome, "Source Sans 3", sans-serif;
        font-weight: 600;
    }

    .indicator {
        position: relative;
        display: inline-block;
        top: 1px;
        padding: 5px;
        border-radius: 6px;

        &.grey {
            border: 1px solid hsl(0deg 0% 80%);
        }

        &.grey-line {
            border: 1px solid hsl(0deg 0% 80%);
            top: 2px;

            &::after {
                content: "";
                background: hsl(0deg 0% 80%);
                height: 1.5px;
                width: 6px;
                display: block;
                margin: 0.5px -2px;
            }
        }

        &.orange {
            border: 1px solid hsl(29deg 84% 51%);
            background: linear-gradient(
                to bottom,
                hsl(0deg 0% 100% / 0%) 50%,
                hsl(29deg 84% 51%) 50%
            );
        }

        &.green {
            border: 1px solid hsl(106deg 74% 44%);
            background-color: hsl(106deg 74% 44% / 30%);
        }

        &.green.solid {
            background-color: hsl(106deg 74% 44%);
        }
    }

    & kbd {
        /* Same as kbd in app_components.css */
        display: inline-block;
        border: 1px solid hsl(0deg 0% 80%);
        border-radius: 4px;
        font-weight: 600;
        white-space: nowrap;
        background-color: hsl(0deg 0% 98%);
        color: hsl(0deg 0% 20%);
        text-shadow: 0 1px 0 hsl(0deg 0% 100%);
        /* Different from app_components.css */
        /* Removed margin setting */
        font-size: 0.85em;
        padding: 0 0.4em;

        &.arrow-key {
            /* Same as in informational_overlays.css */
            line-height: 1;
            padding: 0 0.2em 0.2em;
            /* Different from informational_overlays.css */
            font-size: 1.2em;
        }
    }

    & code {
        /* Same font-family as zulip.css */
        font-family: "Source Code Pro", monospace;
        /* Same as base rules for code elements in rendered_markdown.css */
        font-size: 0.825em;
        unicode-bidi: embed;
        direction: ltr;
        color: hsl(0deg 0% 0%);
        border-radius: 3px;
        /* Different from base rules for code elements in rendered_markdown.css */
        white-space: initial;
        padding: 0 4px;
        background-color: hsl(0deg 0% 93%);
    }

    & pre {
        & code {
            font-size: 14px;
            white-space: pre-wrap;
            padding: 0;
            color: inherit;
            background-color: transparent;
            border: 0;
        }
    }

    .code-section {
        & ol {
            margin-left: 15px;
            margin-top: 10px;
        }

        & ul.nav {
            margin: 0;

            & li {
                display: inline-block;
                padding: 5px 14px;
                margin: 0;

                cursor: pointer;

                &.active {
                    color: hsl(176deg 46% 41%);
                    margin-bottom: -1px;

                    border: 1px solid hsl(0deg 0% 87%);
                    border-bottom: 1px solid hsl(0deg 0% 100%);
                    border-radius: 4px 4px 0 0;
                }
            }
        }

        &.no-tabs ul.nav {
            display: none;
        }

        .blocks {
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid hsl(0deg 0% 87%);

            & > div {
                display: none;
            }
        }

        &.has-tabs .blocks {
            border-radius: 0 6px 6px;
        }

        &.no-tabs .blocks {
            border-radius: 6px;
        }

        &.no-tabs .blocks > div,
        &.has-tabs .blocks > .active {
            display: block;
        }
    }
}

~~~
#### email_log.css ####
~~~
#dev-emails-container {
    .header {
        position: fixed;
    }

    .config-options {
        text-align: right;
    }

    .emails {
        padding-top: 100px;
    }

    #smtp_form_status,
    .hide {
        display: none;
    }

    #forward_email_modal {
        & label.radio {
            padding-left: 20px;
        }

        & input[type="radio"] {
            float: left;
            width: auto;
            cursor: pointer;
            margin: 4px 0 0 -20px;
            line-height: normal;

            &:focus {
                outline: 1px dotted hsl(0deg 0% 20%);
                outline: 5px auto -webkit-focus-ring-color;
                outline-offset: -2px;
            }
        }
    }

    & input[type="checkbox"] {
        width: auto;
        cursor: pointer;

        &:focus {
            outline: 1px dotted hsl(0deg 0% 20%);
            outline: 5px auto -webkit-focus-ring-color;
            outline-offset: -2px;
        }
    }
}

~~~
#### modal.css ####
~~~
.modal-body {
    max-height: 60vh;
}

.modal-bg {
    background-color: hsl(0deg 0% 98%);
}

/* Styles for the Micromodal-based modals */
.modal__overlay {
    position: fixed;
    inset: 0;
    background: hsl(0deg 0% 0% / 60%);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 105;
}

.modal__container {
    display: flex;
    flex-direction: column;
    background-color: hsl(0deg 0% 100%);
    max-width: calc(100% - 32px);
    max-height: 96%;
    width: 32.5rem;
    border-radius: 4px;
    box-sizing: border-box;
}

.modal__header {
    padding: 16px 24px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.modal__footer {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding: 20px 24px;
}

.modal__title {
    margin: 0;
    font-size: 1.375rem;
    font-weight: 600;
    line-height: 1.25;

    /* help_link_widget margin for the fa-circle-o. */
    .help_link_widget {
        margin-left: 5px;
    }
}

.user_profile_name_heading {
    padding-right: 1rem;
    max-width: 80%;
    display: flex;

    .user_profile_name {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }
}

.modal__close {
    &::before {
        content: "\2715";
    }
    margin-right: -4px;
    background: transparent;
    border: 0;

    &:hover {
        background: hsl(0deg 0% 90%);
    }
}

.modal__content {
    display: flex;
    font-size: 1rem;
    overflow-y: auto;
    padding: 0 24px;
    line-height: 1.5;

    &.simplebar-scrollable-y + .modal__footer {
        border-top: 1px solid hsl(0deg 0% 87%);
    }
}

.modal__btn {
    font-size: 0.875rem;
    padding: 0.5rem 1rem;
    background-color: hsl(0deg 0% 90%);
    border-radius: 0.25rem;
    border-width: 0;
    cursor: pointer;
    text-transform: none;
    overflow: visible;
    line-height: 1.15;
    margin: 0;
    will-change: transform;
    backface-visibility: hidden;
    transform: translateZ(0);
    transition: transform 0.25s ease-out;

    &:hover {
        text-decoration: none;
    }

    &:disabled {
        cursor: not-allowed;
    }
}

.modal__btn:focus,
.modal__btn:hover {
    transform: scale(1.05);
}

.dialog_cancel_button {
    background: hsl(0deg 0% 100%);
    border: 1px solid hsl(300deg 2% 11% / 30%);

    &:hover {
        background: hsl(0deg 0% 97%);
    }
}

.dialog_submit_button {
    margin-left: 12px;
    background-color: hsl(240deg 96% 68%);
    color: hsl(0deg 0% 100%) !important;

    &:disabled {
        background-color: hsl(0deg 0% 65%);
    }
}

#read_receipts_error,
#dialog_error {
    margin-bottom: 10px;
}

#read_receipts_modal {
    .modal__container {
        width: 360px;

        .modal__content {
            /* When showing read receipts, we use simplebar
            to make the list scrollable.  It requires this to
            be flex. */
            display: flex;

            /* Setting a minimum height prevents the loading indicator
               appearing/disappearing from resizing the modal in the
               common case that one is requesting read receipts for
               PMs. */
            min-height: 120px;
            /* Setting a maximum height is just for aesthetics; the modal looks
               weird if its aspect ratio gets too stretched. */
            max-height: 480px;

            /* For the notification bot error, we want to keep the modal clean and small.
               The 16px padding is intended to match the padding at the top of the modal. */
            &.compact {
                min-height: unset;
                padding-bottom: 16px;
            }
        }
    }

    .modal__header {
        padding-bottom: 0;
    }

    & hr {
        margin: 10px 0;
    }

    .modal__content {
        padding: 0 24px 8px;
    }

    .loading_indicator {
        margin: auto;
    }

    #read_receipts_list {
        margin-left: 0;

        & li {
            .read_receipts_user_avatar {
                display: inline-block;
                height: 20px;
                width: 20px;
                position: relative;
                right: 8px;
                border-radius: 4px;
            }

            margin: 2px 0;
            list-style-type: none;
            overflow-x: hidden;
            padding-left: 10px;
            white-space: nowrap;
            text-overflow: ellipsis;
            cursor: pointer;
            line-height: 26px;

            &:hover {
                background-color: hsl(0deg 0% 0% / 5%);
            }

            &:active,
            &:focus {
                background-color: hsl(0deg 0% 0% / 10%);
                outline: none;
            }
        }
    }
}

.email_field {
    margin-top: 10px;

    .email_field_textarea {
        width: 97%;
        resize: vertical;
        margin-bottom: 10px;
    }

    .border-top {
        border-top: 1px solid hsl(300deg 2% 11% / 30%);
        padding-top: 10px;
    }

    .email-body {
        margin-left: 20px;
        margin-top: 20px;
    }
}

#select_stream_widget {
    .dropdown-toggle:disabled {
        pointer-events: none;
    }
}

@keyframes mmfadeIn {
    from {
        opacity: 0;
    }

    to {
        opacity: 1;
    }
}

@keyframes mmfadeOut {
    from {
        opacity: 1;
    }

    to {
        opacity: 0;
    }
}

.micromodal {
    display: none;
}

.micromodal.modal--opening,
.micromodal.modal--open {
    display: block;
}

.micromodal[aria-hidden="true"] .modal__overlay {
    animation: mmfadeOut 75ms cubic-bezier(0, 0, 0.2, 1);
}

.micromodal[aria-hidden="false"] .modal__overlay {
    animation: mmfadeIn 120ms cubic-bezier(0, 0, 0.2, 1);
}

.micromodal[aria-hidden="true"] .modal__container {
    animation: mmfadeOut 75ms cubic-bezier(0, 0, 0.2, 1);
}

.micromodal[aria-hidden="false"] .modal__container {
    animation: mmfadeIn 120ms cubic-bezier(0, 0, 0.2, 1);
}

.micromodal .modal__container,
.micromodal .modal__overlay {
    will-change: transform;
}

.modal__spinner .loading_indicator_spinner {
    height: 16px;

    & path {
        fill: hsl(0deg 0% 100%);
    }
}

.modal__spinner {
    display: flex;
    justify-content: center;
}

#copy_email_address_modal {
    width: 800px;

    .inline {
        display: inline;
    }

    .question-which-parts {
        padding-bottom: 10px;
    }

    .stream-email-header {
        font-size: 18px;
    }
}

.modal_select {
    height: 30px;
    width: 220px;
    padding: 4px 6px;
    color: hsl(0deg 0% 33%);
    border-radius: 4px;
    border: 1px solid hsl(0deg 0% 80%);
    cursor: pointer;
    background-color: hsl(0deg 0% 100%);

    &:disabled {
        cursor: not-allowed;

        /* The background-color of select elements inside modal is different than the others in
        settings pages, because the background of the modal is brighter than the setting page. */
        background-color: hsl(0deg 0% 90%);
    }
}

.modal_text_input {
    width: 206px;
}

~~~
#### reactions.css ####
~~~
.message_reactions {
    overflow: hidden;

    user-select: none;

    .message_reaction {
        display: flex;
        float: left;
        margin: 0.15em;
        padding: 0 2px 0 0;
        cursor: pointer;
        background-color: hsl(0deg 0% 100%);
        border: 1px solid hsl(194deg 37% 84%);
        border-radius: 4px;
        align-items: center;

        &.reacted {
            background-color: hsl(195deg 50% 95%);
        }

        &:hover {
            border: 1px solid hsl(200deg 100% 40%);
        }

        + .reaction_button {
            visibility: hidden;
            pointer-events: none;
            margin: 2px 0.1em 3px;
            padding: 3px;
            height: 13px;
            border-radius: 4px;
            padding-left: 0.3em;
            border: 1px solid hsl(0deg 0% 73%);
            padding-right: 0.3em;
            float: left;
        }

        .emoji {
            display: inline-block;
            flex-shrink: 0;
            vertical-align: top;
            top: 0;
            margin: 1px 3px;
            height: 17px;
            width: 17px;
            position: relative;
        }
    }

    .message_reaction_count {
        position: relative;
        top: 1px;
        font-size: 90%;
        display: flex;
        margin: 0 3px;
        padding: 2px 0;
        line-height: 1em;
    }

    .message_reaction:hover .message_reaction_count {
        color: hsl(200deg 100% 40%);
    }

    & i {
        font-size: 1.3em;
        float: left;
        color: hsl(0deg 0% 33%);
    }

    &:hover .message_reaction + .reaction_button {
        visibility: visible;
        pointer-events: all;
        background-color: hsl(0deg 0% 98%);
    }

    .reaction_button {
        display: flex;
        align-items: center;

        & i {
            font-size: 1em;
        }

        &:hover i {
            color: hsl(200deg 100% 40%);
        }

        /* Configure the reaction button to appear if and only if there's an
           existing reaction to the message. We reference first-child
           rather than only-child because tooltips may be appended to
           the DOM after this element, whereas actual reactions are
           appended before it. */
        &:first-child {
            display: none;
        }

        &:hover {
            border: 1px solid hsl(200deg 100% 40%);
            background-color: hsl(195deg 50% 95%);
            cursor: pointer;
            opacity: 1;
            color: hsl(200deg 100% 40%);
        }

        .message_reaction_count {
            font-size: 1.1em;
            color: hsl(0deg 0% 33%);
            margin-right: 0;
        }

        &:hover .message_reaction_count {
            color: hsl(200deg 100% 40%);
        }
    }
}

.private-message .message_reactions .message_reaction {
    background-color: hsl(192deg 20% 95%);

    &.reacted {
        background-color: hsl(196deg 51% 93%);
        border-color: hsl(193deg 38% 70%);
    }
}

.reaction_button_visible {
    visibility: visible !important;
    pointer-events: all !important;
    opacity: 1 !important;
}

.emoji-info-popover {
    padding: 0;
    height: 370px;
    user-select: none;

    .popover-content {
        padding: 0;
    }

    &.bottom .arrow {
        border-bottom-color: hsl(0deg 0% 93%);
    }

    &.top .arrow {
        border-top-color: hsl(0deg 0% 93%);
    }

    .emoji-popover {
        display: block;
        width: 250px;

        .reacted {
            background-color: hsl(195deg 50% 95%);
            border-color: hsl(195deg 52% 79%);
        }

        .emoji-popover-top {
            position: relative;

            padding: 8px 10px;
            margin-bottom: 0;

            background-color: hsl(0deg 0% 93%);

            border-radius: 5px 5px 0 0;

            .fa-search {
                position: absolute;
                color: hsl(0deg 0% 73%);
                top: 15px;
                left: 17px;
                z-index: 3;
            }

            .emoji-popover-filter {
                margin: auto;
                padding-left: 22px;
                width: calc(100% - 22px - 8px);
                font-size: 90%;
            }
        }

        .emoji-popover-category-tabs {
            /* Flex needed here to work around #7511 (90% zoom issues in firefox) */
            display: flex;
            background-color: hsl(0deg 0% 93%);
            width: 100%;
            box-sizing: border-box;
            overflow: hidden;

            .emoji-popover-tab-item {
                display: inline-block;
                padding-top: 8px;
                width: 25px;
                height: 25px;
                text-align: center;
                font-size: 16px;
                cursor: pointer;
                /* Flex needed here to work around #7511 (90% zoom issues in firefox) */
                flex-grow: 1;

                &.active {
                    background-color: hsl(0deg 0% 100% / 20%);
                }
            }
        }

        .emoji-popover-emoji-map,
        .emoji-search-results-container {
            padding: 0;
            position: relative;
            overflow-x: hidden;
            overflow-y: auto;
            display: block;
            width: 247px;
            padding-left: 3px;
        }

        .emoji-search-results-container {
            height: 283px;

            .emoji-popover-results-heading {
                font-weight: 600;
                padding: 5px 3px 3px 5px;
                font-size: 17px;
            }
        }

        .emoji-popover-emoji-map {
            height: 250px;

            .emoji-popover-subheading {
                font-weight: 600;
                padding: 5px 3px;
            }
        }

        .emoji-popover-emoji {
            display: inline-block;
            margin: 0;
            padding: 6px;
            cursor: pointer;
            border-radius: 0.5em;
            height: 25px;
            width: 25px;

            &.reacted.reaction:focus {
                background-color: hsl(195deg 55% 88%);
                outline: none;
            }

            &:not(.reacted):focus {
                background-color: hsl(0deg 0% 93%);
                outline: none;
            }

            &.hide {
                display: none;
            }

            .emoji {
                top: 6px;
            }
        }
    }

    .emoji-showcase-container {
        position: relative;
        background-color: hsl(0deg 0% 93%);
        min-height: 44px;
        width: 250px;

        .emoji-preview {
            position: absolute;
            width: 32px;
            height: 32px;
            left: 5px;
            top: 6px;
            margin-top: 0;
        }

        .emoji-canonical-name {
            position: relative;
            top: 12px;
            margin-left: 50px;
            font-size: 16px;
            font-weight: 600;
            white-space: nowrap;
            text-overflow: ellipsis;
            overflow: hidden;
        }
    }
}

.emoji_alt_code {
    position: relative;
    top: 4px;
    font-size: 0.8em;
    display: inline-block;
    vertical-align: top;
    margin: 0 1px 0 0;
    line-height: 1em;
}

.typeahead .emoji {
    top: 2px;
}

~~~
#### portico_styles.css ####
~~~
@import url("../components.css");
@import url("portico.css");
@import url("portico_signin.css");
@import url("markdown.css");
@import url("navbar.css");
@import url("footer.css");

~~~
#### zulip.css ####
~~~
body,
html {
    width: 100%;
    height: 100%;
    overflow-x: hidden;
    overflow-y: hidden;

    touch-action: manipulation;
}

#app-loading.loaded {
    display: none !important; /* We are now loaded, by definition. */
}

body {
    font-size: 14px;
    line-height: calc(20 / 14);
    font-family: "Source Sans 3", sans-serif;
}

/* Common background color */
body,
#message_view_header_underpadding {
    background-color: hsl(0deg 0% 100%);
    transition: background-color 200ms linear;
}

:root {
    color-scheme: light;

    --color-default-text: hsl(0deg 0% 15%);
    --color-date: hsl(0deg 0% 15% / 75%);

    /*
    This is the header, aka the navbar.
    */
    --header-height: 40px;

    @media (width < $sm_min) {
        --header-height: 30px;
    }

    /*
    We have a 10px gutter below the header,
    which often needs to be respected by both
    the elements above it and below it on
    the y-axis, due to absolute positioning.
    */
    --header-padding-bottom: 10px;

    /*
    Our sidebars (and anything that top-align
    with them) go beneath the header.
    */
    --sidebar-top: calc(var(--header-height) + var(--header-padding-bottom));
    --left-sidebar-collapse-widget-gutter: 10px;
    --left-sidebar-width: 270px;
    --right-sidebar-width: 250px;
}

%dark-theme {
    --color-default-text: hsl(0deg 0% 100%);
    --color-date: hsl(0deg 0% 100% / 75%);
}

:root.dark-theme {
    @extend %dark-theme;
}

@media (prefers-color-scheme: dark) {
    :root.color-scheme-automatic {
        @extend %dark-theme;
    }
}

input,
button,
select,
textarea {
    font-family: "Source Sans 3", sans-serif;
    /* Disable bootstrap size CSS; we want to use our default font size on
       body for input elements. */
    line-height: normal;
    font-size: inherit;
}

blockquote p {
    font-weight: normal;
}

a {
    cursor: pointer;

    &.message_label_clickable:hover {
        cursor: pointer;
        color: hsl(200deg 100% 40%);
    }
}

code,
pre {
    font-family: "Source Code Pro", monospace;
}

.no-select {
    user-select: none;
}

.auto-select {
    user-select: auto;
}

.text-select {
    user-select: text;
}

p.n-margin {
    margin: 10px 0 0;
}

.small-line-height {
    line-height: 1.1;
}

.float-left {
    float: left;
}

.float-right {
    float: right;
}

.float-clear {
    clear: both;
}

.no-margin {
    margin: 0;
}

.history-limited-box {
    color: hsl(16deg 60% 45%);
    border: 1px solid hsl(16deg 60% 45%);
    box-shadow: 0 0 2px hsl(16deg 60% 45%);
}

.all-messages-search-caution {
    border: 1px solid hsl(192deg 19% 75% / 20%);
    box-shadow: 0 0 2px hsl(192deg 19% 75% / 20%);
}

.history-limited-box,
.all-messages-search-caution {
    border-radius: 4px;
    display: none;
    font-size: 16px;
    margin: 0 auto 12px;
    padding: 5px;
    /* Difference should be 16px to accommodate the icon. */
    /* This emulates hanging indent. */
    padding-left: 26px;
    text-indent: -10px;

    & i {
        margin: 0 3px 0 1px;
    }

    & p {
        margin: 0;
        padding: 4px;
    }
}

.bottom-messages-logo {
    display: none;
}

.top-messages-logo {
    /* Since padding under message header is not transparent
       we need to position it below the padding. */
    padding-top: var(--header-padding-bottom);
}

.alert-zulip-logo,
.top-messages-logo,
.bottom-messages-logo {
    width: 24px;
    height: 24px;
    margin: 0 auto 12px;

    & svg {
        & circle {
            fill: hsl(0deg 0% 27%);
            stroke: hsl(0deg 0% 27%);
        }

        & path {
            fill: hsl(0deg 0% 100%);
            stroke: hsl(0deg 0% 100%);
        }
    }
}

#feedback_container {
    display: none;
    position: absolute;
    width: 400px;
    top: 0;
    left: calc(50vw - 220px);
    padding: 15px;

    background-color: hsl(0deg 0% 98%);
    border-radius: 5px;
    box-shadow: 0 0 30px hsl(0deg 0% 0% / 25%);
    z-index: 110;

    animation-name: pulse;
    animation-iteration-count: infinite;
    animation-duration: 2s;

    transition-property: top, bottom;
    transition-duration: 0.5s;

    &.show {
        top: 50px;
    }

    & h3 {
        font-size: 16pt;
        margin-top: 2px;
    }

    .exit-me {
        font-size: 20pt;
        font-weight: 200;
        margin: 0 0 0 10px;
        cursor: pointer;
    }
}

@keyframes pulse {
    0% {
        box-shadow: 0 0 30px hsl(0deg 0% 0% / 35%);
    }

    50% {
        box-shadow: 0 0 30px hsl(0deg 0% 0% / 15%);
    }

    100% {
        box-shadow: 0 0 30px hsl(0deg 0% 0% / 35%);
    }
}

.fade-in-message {
    animation-name: fadeInMessage;
    animation-duration: 1s;
    animation-iteration-count: 1;

    .message_edit_notice {
        animation-name: fadeInEditNotice;
        animation-duration: 1s;
        animation-iteration-count: 1;
    }
}

.message_edit_notice_hover:hover {
    opacity: 1;
}

.header {
    position: fixed;
    z-index: 102; /* Needs to be higher than .alert-bar-container */
    width: 100%;
    height: var(--header-height);
    padding-bottom: var(--header-padding-bottom);
    /* Since the headers are sticky, we need non-transparent background. */
    background-color: hsl(0deg 0% 100%);
}

#top_navbar {
    border-bottom: 1px solid hsl(0deg 0% 0% / 20%);
}

#navbar_alerts_wrapper {
    font-size: 1rem;
    position: relative;

    .alert {
        /* Since alerts are only rendered into the DOM when they are first
           displayed, display: block is the right default for this setting. */
        display: block;
        margin: 0;
        padding-top: 12px;
        padding-bottom: 12px;

        border: none;
        border-radius: 0;

        text-align: center;
        text-shadow: none;
        color: hsl(0deg 0% 100%);

        &.alert-info {
            background-color: hsl(170deg 46% 54%);

            &.red {
                background-color: hsl(0deg 46% 54%);
            }
        }

        .close {
            line-height: 24px;
            position: absolute;
            right: 18px;
            top: 50%;
            transform: translateY(-50%);
        }

        .alert-link {
            color: hsl(169deg 100% 88%);
            font-weight: 600;
        }

        &.red .alert-link {
            color: hsl(0deg 100% 88%);
        }

        .buttons .alert-link {
            margin: 0 5px;
        }
    }
}

#gear-menu .dropdown-menu {
    .org-name,
    .org-url {
        padding: 0 20px;
    }

    .org-info {
        text-align: center;

        & a {
            white-space: normal;
        }
    }

    .org-name {
        font-size: large;
        font-weight: bold;
    }

    .org-url {
        line-height: 100%;
        color: hsl(0deg 0% 52%);
    }

    .org-version {
        padding-top: 3px;
        white-space: normal;
    }

    .org-upgrade {
        color: hsl(226deg 82% 60%);

        & a {
            padding: 0;
        }
    }

    .org-plan,
    .org-upgrade {
        & a {
            line-height: 16px;
        }
    }

    .plan-separator {
        line-height: 8px;
    }

    .small-font-size {
        font-size: 12px;
    }
}

.app {
    width: 100%;
    height: 100%;
    overflow-y: scroll;
    z-index: 99;
    -webkit-overflow-scrolling: touch;
}

.app-main,
.header-main {
    width: 100%;
    /* `max-width` is changed based on `fluid_layout_width` setting in
       `scroll_bar.js`. User may or may not see a flash of mispositioned content
       based on how quickly the JS code is executed. */
    max-width: 1400px;
    min-width: 950px;
    margin: 0 auto;
    padding: 0;
    position: relative;
    background-color: hsl(0deg 0% 100%);
}

.column-right {
    width: var(--right-sidebar-width);
    max-width: var(--right-sidebar-width);
    position: absolute;
    right: 0;
    top: 0;

    .spectator_login_buttons {
        display: flex;
        justify-content: space-evenly;
        position: absolute;
        top: 10px;
        /* width of right column - width of gear icon(250px - 45px) */
        width: 205px;

        & a {
            font-size: calc(16em / 14);
            font-weight: 600;
            color: hsl(0deg 0% 20%);

            &:hover {
                text-decoration: none;
                color: hsl(0deg 0% 0%);
            }

            & i {
                margin-right: 3px;
            }
        }

        .divider {
            color: hsl(0deg 0% 88%);
            font-size: 20px;
            line-height: 1;
        }
    }

    .spectator_narrow_login_button {
        position: absolute;
        top: 0;
        right: 0;
        /* Height of navbar in tablet sizes */
        height: 40px;
        /* Width of userlist-toggle button. */
        width: 45px;
        border-left: 1px solid hsl(0deg 0% 88%);

        .login_button {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
            opacity: 0.5;

            &:hover {
                opacity: 1;
                text-decoration: none;
            }

            & i {
                color: hsl(0deg 0% 20%);
                font-size: 1.6em;
            }
        }
    }
}

.column-left {
    width: var(--left-sidebar-width);
    max-width: var(--left-sidebar-width);
    position: absolute;
    left: 0;
    top: 0;
}

.app-main {
    height: 100%;
    min-height: 100%;

    .column-left .left-sidebar,
    .column-right .right-sidebar {
        position: fixed;
        margin-top: var(--sidebar-top);
        z-index: 100;
    }

    .column-left .left-sidebar {
        width: var(--left-sidebar-width);
        padding-left: var(--left-sidebar-collapse-widget-gutter);
    }

    .column-right .right-sidebar {
        padding-left: 10px;
        width: 240px;
    }

    .column-middle {
        min-height: 100%;
        /* We need `overflow-y: visible` for sticky headers to work. */
    }
}

.column-middle,
#compose-content {
    margin-right: var(--right-sidebar-width);
    margin-left: calc(
        var(--left-sidebar-width) + var(--left-sidebar-collapse-widget-gutter)
    );
    position: relative;
}

textarea,
input {
    font-family: "Source Sans 3", sans-serif;
}

/* Override Bootstrap's fixed sizes for various elements */
textarea,
label {
    font-size: inherit;
    line-height: inherit;
}

/* Bootstrap's focus outline uses -webkit-focus-ring-color which doesn't exist in Firefox */
a:not(:active):focus,
button:focus,
.new-style label.checkbox input[type="checkbox"]:focus ~ span,
i.fa:focus,
i.zulip-icon:focus,
.auto-select:focus,
[role="button"]:focus {
    outline: 2px solid hsl(215deg 47% 50%);
    /* TODO: change solid to auto once the Chromium bug #1105822 is fixed */
}

/* List of text-like input types taken from Bootstrap */
input {
    &[type="text"],
    &[type="password"],
    &[type="datetime"],
    &[type="datetime-local"],
    &[type="date"],
    &[type="month"],
    &[type="time"],
    &[type="week"],
    &[type="number"],
    &[type="email"],
    &[type="url"],
    &[type="search"],
    &[type="tel"],
    &[type="color"] {
        font-size: inherit;
        height: 1.4em;
    }
}

li,
.table th,
.table td {
    line-height: inherit;
}

.btn {
    font-size: inherit;
    height: auto;
    line-height: 100%;
}

/* Classes which style copy buttons */
.copy_button_base {
    outline-color: hsl(0deg 0% 73%);
    height: 18px;
    width: 10px;
    padding: 6px;
    display: block;
    /* The below two avoids the padded element from displaying
    its own border and background color */
    border: none;
    background-clip: content-box;
    /* The z-index here ensures that the copy-message
    icon is clickable and is needed because of reduced
    opacity of readonly textarea */
    z-index: 2;

    &:hover svg path {
        fill: hsl(200deg 100% 40%);
    }
}

.copy_message {
    float: right;
    position: relative;
    cursor: pointer;
    top: 30px;
    /* To make sure the svg doesn't occupy any vertical space. */
    margin-top: -30px;
    right: 2px;
    padding-top: 2px;

    #clipboard_image {
        margin: 0;
    }
}

#copy_generated_invite_link {
    position: relative;
    margin-right: -32px;
    margin-top: -1px;
    padding: 6px 3px 6px 13px;

    /* This property nullifies the box-shadow rendered by .btn class */
    &:active {
        box-shadow: none;
    }
}

#clipboard_image {
    margin-top: -5px;
    margin-left: -8px;
}

/* Classes for hiding and showing controls */

.notdisplayed {
    display: none !important;
}

.notvisible {
    visibility: hidden !important;
    width: 0 !important;
    min-width: 0 !important;
    min-height: 0 !important;
    height: 0 !important;
    overflow: hidden !important;
    position: absolute !important;
}

/* Lighter strong */

strong {
    font-weight: 600;
}

.preserve_spaces {
    white-space: pre-wrap;
}

.sp-input {
    width: calc(100% - 14px);
    box-sizing: initial !important;
}

.logout {
    white-space: nowrap;
}

.sidebar-title {
    color: hsl(0deg 0% 43%);
    font-size: inherit;
    font-weight: normal;
    display: inline;
}

.tooltip {
    &.in {
        font-size: 12px;
        line-height: 1.3;

        opacity: 1;

        &.left {
            margin-left: -12px;
            margin-top: 3px;
        }
    }

    .tooltip-inner {
        background-color: hsl(0deg 0% 7% / 80%);
        padding: 3px 5px;
    }

    /*
    Since hover and click are activated together on touchscreen
    devices, the hover state persists until the next click, creating
    awkward UI where the tooltip sticks around forever :(.

    To resolve this, we just hide the tooltip for touch-events on
    touch-enabled devices resolving the above problem.  This means
    that tooltips will never appear on touchscreen devices, but that's
    probably a reasonable tradeoff here.

    Source: https://drafts.csswg.org/mediaqueries-4/#mf-interaction
    */

    @media (hover: none) {
        visibility: hidden !important;
    }
}

.buddy_list_tooltip_content {
    text-align: left;
    word-wrap: break-word;
}

#message_edit_tooltip {
    float: right;
    color: hsl(0deg 0% 0%);
    margin-top: 2px;
    margin-left: 6px;
    opacity: 0.5;
    cursor: pointer;

    &:hover {
        opacity: 1;
    }
}

.narrow-filter {
    display: block;
    position: relative;
}

.message_header_stream a.message_label_clickable {
    color: inherit;
}

#gear-menu .light-theme {
    display: none;
}

/* .dropdown-menu from v2.3.2
   + https://github.com/zulip/zulip/commit/7a3a3be7e547d3e8f0ed00820835104867f2433d
   basic idea of this fix is to remove decorations from :hover and apply them only
   on :focus. */
.typeahead-menu {
    & li {
        & a {
            display: block;
            padding: 3px 20px;
            clear: both;
            font-weight: normal;
            line-height: 20px;
            color: hsl(0deg 0% 20%);
            white-space: nowrap;

            &:hover {
                text-decoration: none;
            }

            &:focus {
                color: hsl(0deg 0% 100%);
                text-decoration: none;
                background-color: hsl(200deg 100% 38%);
                background-image: linear-gradient(
                    to bottom,
                    hsl(200deg 100% 40%),
                    hsl(200deg 100% 35%)
                );
            }

            /* styles defined for user_circle here only deal with positioning of user_presence_circle
            in typeahead list in order to ensure they are rendered correctly in in all screen sizes.
            Most of the style rules related to color, gradient etc. which are generally common throughout
            the app are defined in user_circles.css and are not overridden here. */
            .user_circle {
                width: 8px;
                height: 8px;
                margin: 0 5px 0 -6px;
                position: relative;
                top: 6px;
                right: 8px;
                display: inline-block;
            }
        }
    }

    .active > a {
        color: hsl(0deg 0% 100%);
        text-decoration: none;
        background-color: hsl(200deg 100% 38%);
        background-image: linear-gradient(
            to bottom,
            hsl(200deg 100% 40%),
            hsl(200deg 100% 35%)
        );
        outline: 0;

        .user_circle_empty {
            border-color: hsl(0deg 0% 25%);
        }
    }

    .active > a:hover {
        text-decoration: none;
    }
}

/* Copied from bootstrap 2.1.1 CSS for dropdown-menu li > a:focus */
li.actual-dropdown-menu > a:focus {
    color: hsl(0deg 0% 100%);
    text-decoration: none;
    background-color: transparent;
    background-image: none;
    filter: none;
    outline: 0;
}

li.actual-dropdown-menu i {
    /* In gear menu, make icons the same width so labels line up. */
    display: inline-block;
    width: 14px;
    text-align: center;
    margin-right: 3px;
}

#gear_menu_about_zulip {
    .white_zulip_icon_without_text {
        position: relative;
        top: 3px;
        width: 14px;
        height: 14px;
        margin-right: 3px;
        filter: invert(20%) sepia(11%) saturate(0%) hue-rotate(272deg)
            brightness(20%) contrast(95%);
    }

    .about_zulip_text {
        position: relative;
        top: 1.4px;
    }

    :hover {
        .white_zulip_icon_without_text {
            filter: none;
        }
    }
}

.settings-dropdown-cog {
    padding: 6px 12px;
}

td.pointer {
    vertical-align: top;
    padding-top: 10px;
    background-color: hsl(0deg 0% 100%);
}

.new_messages {
    background-color: hsl(194deg 53% 79%);
}

.new_messages,
.new_messages_fadeout {
    transition: all 3s ease-in-out;
}

.include-sender {
    .message_edit_notice {
        display: inline-block;
        vertical-align: top;
        line-height: 14px;
        /* A bit of margin here helps these not look associated with the name. */
        margin-left: 4px;
        position: static;
        padding: 0;
        width: auto;
    }
}

.sender-status {
    display: inline-block;
    margin: 8px 0 8px -3px;
    /* this normalizes the margin of the emoji reactions with normal messages. */
    padding-bottom: 5px;
    vertical-align: middle;

    position: relative;
    max-width: calc(100% - 50px);

    .message_edit_notice {
        vertical-align: middle;
    }

    &.sender-status-edit {
        /* Hackery to place the textarea for the message edit form nicely
           for /me messages. */

        vertical-align: top;
        line-height: 0;

        .message_edit_notice {
            line-height: 0;
        }
    }
}

.message_edit_notice {
    font-size: 10px;
    opacity: 0.5;
    user-select: none;
    white-space: nowrap;
    overflow-x: hidden;
    overflow-x: clip;
}

.messagebox-content .message_time {
    display: block;
    font-size: 12px;
    font-weight: normal;
    text-align: right;
    opacity: 0.6;
    color: var(--color-default-text);
    font-feature-settings: "pnum" on, "lnum" on;
    letter-spacing: 0.02em;
    /* Disable blue link styling for the message timestamp link. */
    &:hover {
        text-decoration: none;
        color: var(--color-default-text);
    }
}

/* The way this overrides the menus with a background-color and a high
   z-index is kinda hacky, and requires some annoying color-matching,
   but it works. */
.alert-msg {
    color: hsl(170deg 48% 54%);
    background-color: hsl(0deg 0% 100%);
    z-index: 999;
    font-weight: 400;
    display: none;
}

.status-time {
    top: 8px !important;
}

.message_controls {
    display: inline-block;
    z-index: 1;

    /* This is a bit tricky; we need to reserve space for the message
       controls even when the message isn't hovered, so that hover
       doesn't disturb the layout.  Usually that would be just
       visibility: hidden, but that cannot be animated, so we set
       opacity as well, which can be animated. */
    .message_control_button {
        opacity: 0;
        visibility: hidden;
        transition: all 0.2s ease;
        width: 16px;
        text-align: center;
        display: inline-block;
        position: relative;
        color: hsl(0deg 0% 73%);

        > i {
            vertical-align: middle;
        }
    }

    .actions_hover {
        line-height: 1;

        .zulip-icon-ellipsis-v-solid {
            padding: 2px 5.33px;
            outline: none;
        }
    }

    /* Tooltips should not follow the width restrictions of their parent element. */
    [data-tippy-root] {
        width: max-content;
        word-wrap: unset;
    }

    > .reaction_button {
        &:hover {
            color: hsl(200deg 100% 40%);
        }
    }

    > .view_read_receipts {
        font-size: 14px;
        height: 16px;

        &:hover {
            color: hsl(200deg 100% 40%);
        }
    }

    .edit_content {
        width: 12px;

        &:hover {
            cursor: pointer;
            color: hsl(200deg 100% 40%);
        }
    }

    &.sender-status-controls {
        top: 8px;
    }

    .message_failed {
        display: inline-flex;
        justify-content: space-between;
        cursor: pointer;
        position: relative;
        vertical-align: middle;
        padding-left: 2px;

        &.hide {
            display: none;
        }

        .rotating {
            display: inline-block;
            outline: none;

            animation: rotate 1s infinite linear;
        }

        .failed_message_action {
            opacity: 1 !important;
            color: hsl(0deg 100% 50%);
            font-weight: bold;
            padding: 1px;
        }

        .message_control_button {
            visibility: inherit;
        }
    }

    .star_container {
        &:not(.empty-star) {
            color: hsl(106deg 77% 29%);

            /* Opacity/visibility as though the message is hovered. */
            opacity: 1 !important;
            visibility: visible !important;
        }
    }
}

.star {
    &:hover {
        cursor: pointer;
        color: hsl(153deg 80% 25%);
    }
}

.messagebox {
    position: relative;
    word-wrap: break-word;
    cursor: pointer;
    vertical-align: top;
    border: none;

    &:hover .message_controls,
    &:focus-within .message_controls,
    &:hover .message_failed,
    &:focus-within .message_failed {
        .empty-star:hover {
            cursor: pointer;
        }

        > div {
            opacity: 1;
            visibility: visible;
        }
    }
}

.message_header {
    vertical-align: middle;
    text-align: left;
    /* We can overflow-y if the font size gets big */
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    font-weight: 600;
    line-height: 14px;
    position: relative;
    z-index: 0;
}

.message_list {
    .recipient_row {
        border-bottom: 1px solid hsl(0deg 0% 88%);
        /* This value should be in sync with `margin_between_recipient_rows`
           in `message_list_view`. */
        margin-bottom: 10px;
    }

    .message_header {
        position: sticky;
        top: var(--sidebar-top);
        z-index: 3;
        box-shadow: 0 -1px 0 0 hsl(0deg 0% 100%);
    }
}

.stream_label {
    display: inline-block;
    padding: 4px 6px 3px;
    font-weight: normal;
    height: 17px;
    line-height: 17px;
    border-color: hsl(0deg 0% 0% / 0%) hsl(0deg 0% 0% / 0%) hsl(0deg 0% 0% / 0%)
        hsl(0deg 0% 88%);
    background-color: hsl(0deg 0% 88%);
    border-width: 0;
    position: relative;
    text-decoration: none;

    .recipient-row-stream-icon {
        font-size: 12px;
        line-height: 12px;
    }

    .zulip-icon.zulip-icon-globe {
        position: relative;
        top: 1px;
    }

    &:hover {
        text-decoration: none;
    }

    &::after {
        left: 100%;
        top: 50%;
        content: " ";
        height: 0;
        width: 0;
        position: absolute;
        pointer-events: none;
        margin-top: -11px;
        border-style: solid;
        border-width: 11px 0 11px 5px;
        border-color: inherit;
        z-index: 2;
        transform: scale(0.9999);
    }
}

.stream_topic {
    display: inline-block;
    padding: 3px 3px 2px 9px;
    height: 17px;
    line-height: 17px;
    overflow: hidden;
    text-overflow: ellipsis;
}

.recipient_bar_controls {
    display: flex;
    flex-grow: 1;
    align-items: center;
}

.recipient_row_date {
    color: var(--color-date);
    font-size: calc(12em / 14);
    padding: 0 10px;
    text-align: right;
    display: flex;
    align-items: center;
    font-style: normal;
    font-weight: 600;
    line-height: 17px; /* identical to box height, or 131% */
    letter-spacing: 0.04em;
    text-transform: uppercase;

    /* Display the date when unchanged only for sticky headers. */
    &.recipient_row_date_unchanged {
        display: none;

        .sticky_header & {
            display: block;
        }
    }

    &.hide-date-separator-header {
        display: none;
    }
}

.recipient_bar_icon {
    padding-left: 4px;
    padding-right: 4px;
}

#mark_as_read_turned_off_banner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 8px 8px 8px 14px;
    column-gap: 10px;

    #mark_as_read_turned_off_content {
        margin: 0;
        flex-grow: 1;
    }

    #mark_as_read_controls {
        display: flex;
    }

    #mark_as_read_close {
        align-self: flex-start;
        margin-top: -5px;
        /* override bootstrap */
        top: 0;
        right: 0;
        position: static;
    }
}

.copy-paste-text {
    /* Hide the text that we want copy paste to capture */
    position: absolute;
    text-indent: -99999px;
    float: left;
    width: 0;
}

@keyframes rotate {
    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(359deg);
    }
}

@keyframes fadeInMessage {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}

@keyframes fadeInEditNotice {
    0% {
        transform: translateX(-10px);
    }

    100% {
        transform: translateX(0);
    }
}

.message_header_private_message {
    background-color: hsl(0deg 0% 100%);

    .message_label_clickable {
        background-color: hsl(0deg 0% 27%);
        display: inline-block;
        padding: 3px 6px 2px;
        font-weight: normal;
        height: 17px;
        line-height: 17px;
        border-left-color: hsl(0deg 0% 27%);
    }

    /* Base color backgrounds for message boxes,
       private messages, mentions, and unread messages */

    .message-header-contents {
        background-color: hsl(192deg 19% 75% / 20%);
        box-shadow: inset 1px 1px 0 hsl(0deg 0% 88%);
    }
}

.private-message {
    .alert-msg {
        background-color: hsl(192deg 20% 95%);
    }

    .messagebox,
    .date_row {
        background-color: hsl(192deg 19% 75% / 20%);
        /* The 5th parameter here is a spread-radius, which, when negative,
         * causes the shadow to shrink (be smaller than the target
         * element), resulting in a visual width of 3px-1px=2px. This
         * is a workaround for a regression found in Electron
         * v18.3.15+ where the box-shadow with spread-radius >= 0
         * would cause horizontal separator lines to appear between
         * messages in the color of the left ruler. The root cause of
         * that regression is yet unknown.
         *
         * Similar CSS for stream messages is present directly in the
         * Handlebars templates, since the color used there is the
         * stream's configured color.
         */
        box-shadow: inset 3px 0 0 -1px hsl(0deg 0% 27%),
            -1px 0 0 0 hsl(0deg 0% 27%);
    }
}

.message-header-contents {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-right: 1px solid hsl(0deg 0% 88%);
    background-color: hsl(0deg 0% 88%);
}

.group_mention .messagebox,
.direct_mention .messagebox {
    background-color: hsl(8deg 94% 94%);
}

.recipient_row .message_row:first-child .unread_marker {
    top: 0;
}

.unread_marker {
    display: block;
    position: absolute;
    height: 100%;
    left: 2px;
    top: 0;
    opacity: 0;
    z-index: 2;
    bottom: 1px;
    transition: all 0.3s ease-out;

    &.slow_fade {
        transition: all 2s ease-out;
    }

    &.fast_fade {
        transition: all 0.3s ease-out;
    }
}

.unread-marker-fill {
    background-color: hsl(107deg 74% 29%);
    width: 3px;
    height: 100%;
}

.unread .unread_marker {
    transition: all 0.3s ease-out;
    opacity: 1;
}

.message_header + .selected_message {
    /* Sticky message header overlaps 1px with the box-shadow, so we add another
       2px wide box-shadow 1px below from top to compensate for that. */
    .messagebox-content {
        box-shadow: inset 0 1px 0 2px hsl(215deg 47% 50%),
            inset 0 0 0 2px hsl(215deg 47% 50%), 0 0 0 1px hsl(215deg 47% 50%);
    }
}

.selected_message {
    .messagebox-content {
        box-shadow: inset 0 0 0 2px hsl(215deg 47% 50%),
            0 0 0 1px hsl(215deg 47% 50%);
    }
}

.message_sender {
    & i.zulip-icon.zulip-icon-bot {
        font-size: 12px;
    }
}

.sender_name {
    display: inline-block;
    font-weight: 700;
}

.sender_name-in-status {
    margin-right: 3px;
    font-weight: 700;
}

.sender_name_hovered {
    .sender_name,
    .sender_name-in-status {
        color: hsl(200deg 100% 40%);
    }
}

.actions_hover:hover {
    color: hsl(200deg 100% 40%);
}

.always_visible_topic_edit,
.on_hover_topic_read,
.on_hover_topic_unmute {
    opacity: 0.7;

    &:hover {
        cursor: pointer;
        opacity: 1;
    }
}

.on_hover_topic_edit,
.on_hover_topic_unresolve,
.on_hover_topic_resolve,
.on_hover_topic_mute {
    opacity: 0.2;

    &:hover {
        cursor: pointer;
        opacity: 0.7;
    }
}

/* Make the action icon on the message row
   always visible while the popover is open */
.has_actions_popover .actions_hover {
    visibility: visible !important;
    pointer-events: all !important;
    opacity: 1 !important;

    & i:focus {
        /* Avoid displaying a focus outline outside the popover on the \vdots
           icon when opened via the mouse. */
        outline: 0 !important;
    }
}

.has_actions_popover .info {
    opacity: 1;
    visibility: visible;
}

/* Brighten text because of the dark background */
.dark_background a,
.dark_background a:hover,
a.dark_background:hover,
.dark_background {
    color: hsl(0deg 0% 100%) !important;
}

.dark_background a.message_label_clickable:hover {
    color: hsl(200deg 99% 60%);
}

.small {
    font-size: 80%;
}

.tiny {
    font-size: 60%;
}

.settings-forgot-password {
    display: inline-block;
    position: relative;
    color: hsl(0deg 0% 73%);
    bottom: 4px;
}

div.message_table {
    border-collapse: separate;
    margin-left: auto;
    display: none;
    width: 100%;
}

.message_row {
    position: relative;
    border-left: 1px solid hsl(0deg 0% 0% / 10%);
    border-right: 1px solid hsl(0deg 0% 0% / 10%);

    .date_row {
        /* We only want padding for the date rows between recipient blocks */
        padding-bottom: 0;

        & span {
            font-size: calc(12em / 14);
            font-style: normal;
            font-weight: 600;
            line-height: 17px; /* identical to box height, or 131% */
            text-align: right;
            letter-spacing: 0.04em;
            color: var(--color-date);
        }
    }
}

div.focused_table {
    display: block;
}

.message_content {
    line-height: 1.214;
    min-height: 17px;
    display: block;
    position: relative;
    overflow: hidden;

    &:empty {
        display: none;
    }

    &.condensed {
        max-height: 8.5em;
        min-height: 0;
        overflow: hidden;
    }

    &.collapsed {
        max-height: 0;
        min-height: 0;
        overflow: hidden;
    }
}

.rtl {
    direction: rtl;
}

.message_edit_content {
    line-height: 18px;
    resize: vertical !important;
    max-height: 24em;
}

.message_edit_countdown_timer {
    text-align: right;
    display: inline;
    color: hsl(0deg 0% 63%);
}

.message_edit_tooltip {
    display: inline;
    color: hsl(0deg 0% 63%);
}

.message-edit-timer {
    float: right;
    display: none;
    margin-top: 5px;
}

.message-edit-feature-group {
    display: inline-flex;
    margin: 0 auto -5px 10px;
    align-items: baseline;
}

.message_edit_save .loader {
    display: none;
    vertical-align: top;
    position: relative;
    height: 28px;
    margin-top: -10px;
    top: 6px;
    width: 30px;
}

.edit-controls {
    .btn-wrapper {
        cursor: not-allowed;
    }

    .disable-btn {
        pointer-events: none;
    }
}

.topic_edit {
    display: none;
    line-height: 22px;

    .alert {
        display: inline-block;
        margin: 0;
        padding: 0 10px;
        line-height: 17px;
    }
}

#inline_topic_edit {
    margin-bottom: 5px;
    width: 206px;

    &.header-v {
        height: 18px;
        display: inline-block;
        padding: 0 3px;
        vertical-align: baseline;
        line-height: 0px;
        box-shadow: none;
    }
}

#message_edit_topic {
    margin: 0 5px 10px 0;
}

.message_edit_header {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
}

#inline_topic_edit:focus,
#message_edit_topic:focus {
    outline: none;
}

#move_topic_modal select {
    width: auto;
    margin-bottom: 10px;
    max-width: 100%;
}

.topic_move_breadcrumb_messages,
.message_edit_breadcrumb_messages {
    margin: 0 5px 5px 0;
    align-self: center;
    width: 100%;
    white-space: nowrap;

    & label.checkbox {
        /* Place the checkboxes on their own lines. */
        display: block;

        & input {
            margin: 0;
            vertical-align: baseline;
        }

        & + label.checkbox {
            margin-top: 10px;
        }
    }

    & label {
        display: inline-block;
        margin-right: 10px;
    }
}

.message_edit_breadcrumb_messages {
    margin-bottom: 10px;
}

.message_length_controller {
    display: none;
    text-align: center;
    color: hsl(200deg 100% 40%);

    /* to make message-uncollapse easier */
    margin-top: 10px;

    &:hover {
        text-decoration: underline;
    }
}

.bookend {
    margin-top: 10px;
    background-color: transparent;
}

.inline_profile_picture {
    display: inline-block;
    width: 35px;
    height: 35px;
    margin-right: 11px;
    vertical-align: top;
    border-radius: 4px;
    overflow: hidden;

    &.guest-avatar::after {
        outline: 2px solid hsl(0deg 0% 100%);
    }
}

.home-error-bar {
    margin-top: 5px;
    display: none;

    .alert {
        margin-bottom: auto;
    }
}

.streamname {
    font-weight: bold;
}

.top-navbar-border {
    border-right: 1px solid hsl(0deg 0% 88%);
    border-left: 1px solid hsl(0deg 0% 88%);
}

.search_icon {
    /* These rules match the .dropdown-toggle CSS for the gear menu. */
    color: inherit;
    opacity: 0.5;
    text-decoration: none;

    &:hover {
        opacity: 1;
    }
}

#message_view_header {
    z-index: 2;
    float: left;
    height: var(--header-height);
    width: 100%;
    line-height: var(--header-height);
    font-size: 16px;
    display: flex;
    align-content: flex-start;
    flex-wrap: nowrap;
    margin: 0;
    border: none;
    white-space: nowrap;
    cursor: default;

    .hidden {
        display: none;
    }

    .zulip-icon.zulip-icon-globe {
        font-size: 14px;
        position: relative;
        top: 1px;
    }

    .sub_count,
    .stream,
    & > span {
        white-space: nowrap;
        list-style-type: none;
        display: inline-block;
        vertical-align: top;
        position: relative;
        font-weight: 600;
        font-size: 16px;
        line-height: 16px;
        margin: 0 -4px 0 0;
        padding: 12px 6px;
        overflow: hidden;
        text-overflow: ellipsis;

        @media (width < $sm_min) {
            padding: 7px 3.5px; /* based on having ~41.66% decrease */
        }

        & i {
            margin: 0 3px 0 5px;
        }

        .fa {
            &.fa-lock {
                position: relative;
                top: 0.5px;
            }

            .fa-envelope {
                font-size: 14px;
                margin: 0 5px;
            }

            .fa-hashtag {
                font-size: 1.2rem;
                /* font-weight: 800; */
                margin: 0 2px 0 5px;
            }
        }
    }

    .stream {
        text-overflow: clip;
        color: inherit;
        text-decoration: none;
        /* The first ~3px of padding here overlaps with the left padding from sub_count for some reason. */
        padding-right: calc(3px + 10px);
    }

    .divider {
        color: hsl(0deg 0% 88%);
        font-size: 20px;
        margin: 0 3px;
    }

    .sub_count,
    .narrow_description {
        background: none;
        font-size: 14px;
        color: hsl(0deg 0% 40%);
        font-weight: 400;
        line-height: 20px;
    }

    .sub_count {
        padding-left: 10px;
        margin-left: 1px;
        padding-right: 10px;
        margin-right: 1px;
        overflow: visible;

        .fa.fa-user-o {
            margin-left: 0;
        }

        &::before,
        &::after {
            content: "|";
            position: absolute;
            top: 25%;
            height: 50%;
            color: hsl(0deg 0% 88%);
            font-size: 20px;

            @media (width < $sm_min) {
                top: 10%;
            }
        }

        &::before {
            left: -3px;

            @media (width < $sm_min) {
                /* this ensures the before "|" doesn't overlap
                   with the stream name text on small narrows */
                left: 0;
            }
        }

        &::after {
            right: -3px;
        }
    }

    .narrow_description {
        /* the actual value of flex shrink does not matter, it is the
           ratio of this value to other flex items that determines the
           behavior while shrinking, here the other item has the .stream
           class and a flex of 1, so the value here *is* the ratio, and
           is chosen such that the narrow description shrinks to close
           before the stream name must begin to shrink */
        flex-shrink: 100;
        white-space: nowrap;
        margin: 0;
        padding: 12px 0;
        padding-left: 10px;

        @media (width < $sm_min) {
            padding: 7px 0;
            padding-left: 10px;
        }

        & > a {
            padding: 12px 0;
        }
    }

    .search_closed {
        overflow: visible;
        flex: 0; /* makes sure search icon is always visible */

        cursor: pointer;
        font-size: 20px;

        padding: 10px 15px 0 0;

        @media (width < $sm_min) {
            padding: 5px 15px 0 0;
        }
    }

    /* The very last element in the navbar is the search icon, the second
       last element is either the narrow description (for stream narrows) or
       the "title" (for other narrows). The flex-grow property ensures these
       elements take up the entirety of the white space. */
    .navbar-click-opens-search {
        flex-grow: 1;

        /* Provide the visual cue that clicking this will work as expected. */
        cursor: pointer;

        &:hover ~ .search_closed {
            opacity: 1;
        }
    }
}

#navbar-buttons {
    white-space: nowrap;
    margin-left: 15px;
    margin-top: 7px;
    display: inline-block;
    float: right;

    & ul.nav {
        margin: 0;

        .dropdown-toggle,
        li.active .dropdown-toggle {
            font-size: 20px;
            color: inherit;
            opacity: 0.5;
            text-shadow: none;
            padding-left: 0 !important;
            background-color: inherit;
            box-shadow: inherit;
            display: block;
            position: absolute;
            right: 6px;
            top: -3px;
        }

        .dropdown-toggle:hover,
        li.active .dropdown-toggle:hover {
            opacity: 1;
        }

        & li.dropdown.open .dropdown-toggle {
            background: none;
            opacity: 1;
            text-shadow: none;
        }

        & li.dropdown li.divider {
            margin-left: 15px;
            margin-right: 15px;
        }
    }
}

#streamlist-toggle {
    display: none;
    position: absolute;
    top: 0;
    left: 0;
    text-align: center;
    vertical-align: middle;
    /* border-right: 2px solid hsl(204, 20%, 74%); */
}

.hide-streamlist-toggle-visibility,
.hide-navbar-buttons-visibility {
    visibility: hidden;
}

#streamlist-toggle-button {
    text-decoration: none;
    color: hsl(0deg 0% 52%);
    display: block;
    position: relative;
    background-color: hsl(0deg 0% 89%);
    width: 40px;
    height: 19px;
    padding-top: 12px;
    padding-bottom: 9px;
}

#streamlist-toggle-unreadcount,
#userlist-toggle-unreadcount {
    position: absolute;
    display: none;
    height: 12px;
    min-width: 12px;
    line-height: 12px;
    background-color: hsl(0deg 100% 20%);
    top: 4px;
    right: 4px;
    border: 1px solid hsl(0deg 0% 93%);
    box-shadow: 0 0 1px hsl(0deg 0% 0% / 20%);
    border-radius: 12px;
    padding: 1px;
    font-size: 9px;
    z-index: 15;
    font-weight: normal;
    color: hsl(0deg 0% 100%);
}

.nav .dropdown-menu {
    left: auto;
    right: 0;
    top: 30px;
    /* Match the width of the right sidebar so that we don't have
       the presence dots distracting you when looking at this. */
    min-width: 240px;
    box-shadow: 0 0 5px hsl(0deg 0% 0% / 20%);

    &::after {
        position: absolute;
        width: 0;
        height: 0;
        top: -7px;
        right: 19px;
        display: inline-block;
        border-right: 7px solid transparent;
        border-bottom: 7px solid hsl(0deg 0% 67%);
        border-left: 7px solid transparent;
        content: "";
        z-index: 10;
    }
}

#gear-menu .zulip-icon-language {
    position: relative;
    top: 2.5px;
    left: -0.5px;
}

.nav .dropdown-menu a,
.typeahead.dropdown-menu a {
    color: inherit;
}

.typeahead.dropdown-menu {
    .active {
        color: hsl(0deg 0% 100%);

        .unsubscribed_icon {
            display: block;
            float: right;
            margin-top: 5px;
            margin-right: -12px;
            font-size: 0.8em;
            color: hsl(96deg 7% 73%);
        }
    }

    .unsubscribed_icon {
        display: none;
    }
}

.typeahead-image {
    display: inline-block;
    height: 21px;
    width: 21px;
    position: relative;
    margin-top: -4px;
    vertical-align: middle;
    top: 2px;
    right: 8px;
    border-radius: 4px;

    /* For FontAwesome icons used in place of images for some users. */
    font-size: 19px;
    text-align: center;

    &.no-presence-circle {
        margin-left: 9px;
        top: 3px;
    }
}

nav {
    .column-left {
        text-align: center;

        .nav-logo {
            display: inline-block;
            vertical-align: top;
            margin-top: 8px;
            height: 25px;
            max-width: 200px;
        }
    }

    & a {
        &.no-style:hover {
            text-decoration: none;
            cursor: pointer;
        }

        .no-style {
            text-decoration: none;
        }
    }
}

#bottom_whitespace {
    display: block;
    height: 300px;
}

.operator_value {
    font-family: "Source Code Pro", monospace;
    color: hsl(353deg 70% 65%);
}

.operator {
    font-family: "Source Code Pro", monospace;
}

#loading_older_messages_indicator,
#loading_newer_messages_indicator {
    margin: 10px;
}

#loading_older_messages_indicator_box_container,
#loading_newer_messages_indicator_box_container {
    position: absolute;
    left: 50%;
}

#loading_older_messages_indicator_box,
#loading_newer_messages_indicator_box {
    position: relative;
    left: -50%;
    top: -43px;
    z-index: 1;
    border-radius: 6px;
}

#page_loading_indicator {
    margin: 10px auto;
}

#page_loading_indicator_box_container {
    position: absolute;
    left: 50%;
}

#page_loading_indicator_box {
    position: relative;
    left: -50%;
    top: -43px;
    z-index: 1;
    border-radius: 6px;
}

#create_stream_subscribers {
    margin-top: 10px;

    .checkbox {
        display: block;

        & input[type="checkbox"] {
            margin: 5px 0;
            float: none;
        }
    }
}

.sub_button_row {
    text-align: center;
}

.small_square_button {
    padding: 0;
    border: none;
    font-size: 12px;
    width: 18px;
    height: 18px;
    border-radius: 4px;
    margin-bottom: 3px;

    &:focus {
        outline: none;
    }

    &.small_square_x {
        background-color: hsl(0deg 0% 100%);
        color: hsl(0deg 0% 47%);

        &:hover {
            color: hsl(0deg 0% 18%);
        }
    }
}

div.topic_edit_spinner {
    display: inline-block;
    width: 18px;
    height: 18px;
    margin-top: -1px;
    padding: 2px;
    vertical-align: middle;
}

div.topic_edit_spinner .loading_indicator_spinner {
    width: 14px;
    height: 14px;
}

.message_edit_spinner {
    margin-right: 8px;
    padding-top: 5px;
}

.message_edit_spinner .loading_indicator_spinner {
    width: 20px;
    height: 20px;
}

textarea.invitee_emails {
    min-height: 40px;
    max-height: 300px;
    width: 96%;
    max-width: 96%;
    resize: vertical !important;

    color: hsl(0deg 0% 33%);
    background-color: hsl(0deg 0% 100%);
    border-radius: 4px;
    vertical-align: middle;
    border: 1px solid hsl(0deg 0% 80%);
    padding: 4px 6px;

    box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%);
    transition: border linear 0.2s, box-shadow linear 0.2s;

    &:focus {
        border-color: hsl(206.5deg 80% 62% / 80%);
        outline: 0;

        box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%),
            0 0 8px hsl(206.5deg 80% 62% / 60%);
    }

    &:disabled {
        cursor: not-allowed;
        background-color: hsl(0deg 0% 93%);
    }
}

#invite-user-modal {
    #custom-expiration-time-input,
    #invite-user-form {
        margin: 0;
    }
}

select.invite-expires-in,
select.custom-expiration-time,
select.invite-as {
    width: 220px;
    height: 30px;
    padding: 4px 6px;
    color: hsl(0deg 0% 33%);
    border-radius: 4px;
    border: 1px solid hsl(0deg 0% 80%);
    cursor: pointer;
    background-color: hsl(0deg 0% 100%);
    vertical-align: middle;
}

#multiuse_invite_link {
    width: 370px;
    text-overflow: ellipsis;
    white-space: nowrap;
    display: inline-block;
    overflow: hidden;
    vertical-align: bottom;
}

#invite-stream-checkboxes {
    & i.zulip-icon-globe {
        font-size: 80%;
    }
}

#invite-method-choice {
    margin-top: 2px;
}

#multiuse_radio_section {
    margin-top: 4px;
    margin-bottom: -2px;
    display: none;
}

#generate_multiuse_invite_button {
    position: relative;
    top: 1px;
}

#custom-invite-expiration-time {
    #custom-expiration-time-input {
        width: 5ch;
        margin-right: 15px;
    }

    #custom-expiration-time-unit {
        width: auto;
    }
}

.empty_feed_notice {
    padding: 3em 1em;
    text-align: center;
}

.message-fade,
.user_sidebar_entry.user-fade {
    opacity: 0.4;
}

.emoji {
    height: 25px;
    width: 25px;
    position: relative;
    margin-top: -7px;
    vertical-align: middle;
    top: 3px;
}

.status-emoji {
    height: 16px;
    width: 16px;
    /* We are setting minimum width here because when the user's name is very long,
    emoji's width decreases and causes it to break. */
    min-width: 16px;
    /* In most contexts, status emoji appear immediately after a name
      field with no margin. Position the status emoji with 3px of left
      margin to space it from the name, and set no right margin so
      that any components to the right appear equally distant as they
      would be from a name. */
    margin-left: 3px;
    margin-right: 0;
}

/* FIXME: Combine this rule with the one in portico.css somehow? */
#pw_strength {
    width: 100%;
    height: 10px;
    margin-bottom: 0;
}

#pw_change_controls {
    display: none;
}

.sub-unsub-message,
.date_row {
    padding-bottom: 10px;
}

.date_row {
    padding-left: 2px;
    text-align: right;
}

.sub-unsub-message span,
.date_row span {
    display: block;
    padding: 4px;
    overflow: hidden;
    text-transform: uppercase;
}

.sub-unsub-message .stream-status {
    opacity: 0.6;
}

.sub-unsub-message {
    text-align: center;
}

.sub-unsub-message span {
    font-size: 1em;
    text-transform: none;
}

.sub-unsub-message span::before,
.sub-unsub-message span::after,
.date_row span::before,
.date_row span::after {
    display: inline-block;
    position: relative;
    content: " ";
    vertical-align: middle;
    height: 0;
    opacity: 0.35;
    border-bottom: 1px solid hsl(0deg 0% 0%);
}

.sub-unsub-message span::before,
.sub-unsub-message span::after {
    width: 50%;
}

.date_row span::before {
    width: 100%;
}

.date_row span::after {
    width: 6px;
    left: 0.25em;
}

.sub-unsub-message span::before,
.date_row span::before {
    right: 0.25em;
    margin-left: -50%;
}

.sub-unsub-message span::after {
    left: 0.25em;
    margin-right: -50%;
}

.message_edit {
    display: none;
}

/* Reduce some of the heavy padding from Bootstrap. */
.message_edit_form {
    margin-bottom: 10px;
    cursor: default;

    .edit-controls {
        margin-left: 0;
        margin-top: 0;
    }

    /* Override the default border-radius to properly align
       the button corners with `stream_header_colorblock`. */
    .dropdown-toggle {
        border-radius: 1px 4px 4px 1px !important;
    }

    .dropdown-list-widget,
    .stream_header_colorblock {
        margin-bottom: 10px;
    }

    & textarea {
        width: 100%;
        min-width: 206px;
        box-sizing: border-box;
        /* Setting resize as none hides the bottom right diagonal box
           (which even has a background color of its own!). */
        resize: none !important;
        color: hsl(0deg 0% 33%);
        background-color: hsl(0deg 0% 100%);
        border-radius: 4px;
        vertical-align: middle;
        border: 1px solid hsl(0deg 0% 80%);
        padding: 4px 6px;
        margin-bottom: 10px;

        box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%);
        transition: border linear 0.2s, box-shadow linear 0.2s;

        &:focus {
            border-color: hsl(206.5deg 80% 62% / 80%);
            outline: 0;

            box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%),
                0 0 8px hsl(206.5deg 80% 62% / 60%);
        }

        &:read-only,
        &:disabled {
            cursor: not-allowed;
            background-color: hsl(0deg 0% 93%);
        }
    }
}

#topic_edit_form {
    display: inline-block;
    margin: 0;
    height: 22px;
    padding-left: 20px;
    padding-right: 3px;
    line-height: 22px;
    margin-left: -15px;
}

#message_feed_container {
    padding-top: var(--sidebar-top);
}

.screen {
    position: absolute;
    left: 0;
    top: 0;
    background-color: hsl(0deg 0% 0%);
    z-index: 20000;
}

.deactivated_user .deactivated-user-icon {
    color: inherit;
    margin-left: 2px;
    font-size: 0.9em;
}

.no-drag {
    -webkit-user-drag: none;
    user-select: none;
}

.user_popover_email {
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    transition: all 0.4s ease;

    & i {
        cursor: pointer;

        &.hide_copy_icon {
            display: none;
        }
    }
}

.email_copied,
.user_popover_email i:hover {
    color: hsl(170deg 48% 54%);
}

.email_copied i {
    display: none !important;
}

.flatpickr-calendar {
    /* Hide the up and down arrows in the Flatpickr datepicker year */
    .flatpickr-months .numInputWrapper span {
        display: none;
    }

    .flatpickr-time-separator {
        position: relative;
        left: 5px;
    }

    .flatpickr-time input {
        margin: 0 5px;
        min-height: 30px;
    }

    .flatpickr-confirm {
        color: hsl(0deg 0% 100%);
        background-color: hsl(213deg 90% 65%);
        font-size: 18px;
        font-weight: 600;
    }

    @media (width < $md_min) {
        /* Center align flatpickr on mobile
         * devices so that it doesn't go out of
         * the viewport. */
        left: 0 !important;
        right: 0 !important;
        margin: auto;

        &::after,
        &::before {
            border-top-width: 0 !important;
        }
    }
}

#about-zulip {
    .exit {
        font-size: 1.5rem;
        font-weight: 600;
        background-color: transparent;
        border: none;
        position: absolute;
        right: 8px;
        z-index: 1;
        color: hsl(0deg 0% 67%);
    }

    .overlay-content {
        width: 440px;
        border-radius: 4px;
    }

    .about-zulip-logo {
        text-align: center;
        margin: 30px;
    }

    .about-zulip-logo img {
        height: 40px;
    }

    & i.fa-copy {
        cursor: pointer;
    }
}

@media (width < $xl_min) {
    .app-main,
    .header-main {
        min-width: 750px;
    }

    .column-right {
        display: none;

        &.expanded {
            display: block;
            position: absolute;
            float: none;
            right: 15px;
            top: 0;

            .right-sidebar {
                background-color: hsl(0deg 0% 100%);
                box-shadow: 0 -2px 3px 0 hsl(0deg 0% 0% / 10%);
                border-left: 1px solid hsl(0deg 0% 87%);

                /* We use both margin and padding to
                   hide little artifacts from showing up in
                   the gutter below the navbar. */
                margin-top: var(--header-height);
                padding: var(--header-padding-bottom) 15px 0 15px;
                height: 100%;
                right: 0;
            }
        }
    }

    .header-main .column-right {
        display: inline-block;
        width: 30px;
    }

    #top_navbar #navbar-buttons {
        margin-right: 41px;
    }

    .nav .dropdown-menu {
        min-width: 180px;
        box-shadow: 0 0 5px hsl(0deg 0% 0% / 20%);

        &::after {
            right: 21px;
        }
    }

    .column-middle {
        margin-right: 7px;
    }

    .top-navbar-container {
        width: calc(100% - 84px);
    }

    .search_closed .zulip-icon-search {
        right: 115px;
    }
}

@media (width < $md_min) {
    body {
        padding: 0;
    }

    .column-left {
        display: none;

        &.expanded {
            display: block;
            position: absolute;
            float: none;
            left: 0;
            top: 0;

            .left-sidebar {
                background-color: hsl(0deg 0% 100%);
                box-shadow: 0 2px 3px 0 hsl(0deg 0% 0% / 10%);
                border-right: 1px solid hsl(0deg 0% 87%);

                /* We use both margin and padding to
                   hide little artifacts from showing up in
                   the gutter below the navbar. */
                margin-top: var(--header-height);
                padding-top: var(--header-padding-bottom);

                height: 100%;
                padding-left: 10px;
                width: var(--left-sidebar-width);
            }
        }
    }

    body,
    html,
    .app-main,
    .header-main {
        min-width: 350px;
    }

    .column-middle,
    .app-main .column-middle {
        margin-left: 7px;
        margin-right: 7px;
    }

    .header-main .column-middle {
        margin-left: 0;
    }

    .column-middle-inner {
        margin-left: 0;
        margin-right: 15px;
    }

    .app-main .column-middle .column-middle-inner {
        margin-right: 0;
    }

    #streamlist-toggle {
        display: block;
    }

    .top-navbar-border {
        margin-left: 40px;
        width: calc(100% - 108px);
    }

    .search_closed .zulip-icon-search {
        right: 115px;
    }
}

@media (width < $sm_min) {
    .column-right.expanded .right-sidebar,
    .column-left.expanded .left-sidebar {
        margin-top: 31px;
    }

    .column-left.expanded {
        .left-sidebar {
            padding: 0;

            #streams_header {
                padding-right: 10px;
            }
        }

        .narrows_panel {
            margin-top: 10px;
        }
    }

    /* Usually the styling is applied directly to the icon, but here
    the icon is `position: static`, so we can't. */
    .search_closed {
        top: 4px;
    }

    #streamlist-toggle,
    #navbar-buttons,
    .navbar-search,
    #message_view_header,
    #searchbox,
    #searchbox_legacy,
    .header {
        line-height: var(--header-height);
        height: var(--header-height);
    }

    .spectator_narrow_login_button {
        height: var(--header-height) !important;
    }

    #streamlist-toggle-button {
        height: var(--header-height);
        padding-top: 0;
        padding-bottom: 0;
    }

    #navbar-buttons ul.nav .dropdown-toggle,
    #navbar-buttons ul.nav li.active .dropdown-toggle {
        top: -8px;
    }

    .messagebox-content {
        padding-right: 15px;
    }

    .include-sender .message_controls {
        background: none !important;
        padding: 0 !important;
        border: none !important;
    }

    #floating_recipient_bar {
        top: var(--sidebar-top);
    }

    .message_content {
        padding-right: 50px;
    }
}

@media (width < $mm_min) {
    html {
        overflow-x: hidden;
    }

    body,
    html,
    .app-main,
    .header-main {
        min-width: 320px;
    }
}

@media (width < $md_min) {
    #feedback_container {
        width: calc(90% - 30px);
        left: 5%;
        top: 5%;
    }
}

#scroll-to-bottom-button-container {
    display: block;
    position: absolute;
    bottom: 41px;
    right: 0;
    visibility: hidden;
    opacity: 0;
    transition: visibility 500ms, opacity 500ms ease-in-out;

    &.show {
        visibility: visible;
        opacity: 1;
    }

    #scroll-to-bottom-button-clickable-area {
        width: 60px;
        height: 60px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;

        &:hover #scroll-to-bottom-button {
            background: hsl(240deg 96% 68%);
        }

        #scroll-to-bottom-button {
            text-align: center;
            width: 40px;
            height: 40px;
            background: hsl(240deg 96% 68% / 50%);
            border-radius: 50%;

            & i {
                color: hsl(0deg 0% 100%);
                margin: 0 auto;
                font-size: 21px;
                position: relative;
                top: 8px;
            }
        }
    }
}

.tooltip_right_arrow {
    position: relative;
    top: -1px;
    font-weight: 600;
}

.spectator_login_for_image_button {
    max-width: 250px;
    height: 50px;

    :hover {
        text-decoration: none;
    }

    .login_button {
        padding: 5px;
        margin-top: 5px;

        .fa {
            top: 1px;
        }
    }
}

.recipient_row {
    /* See https://stackoverflow.com/questions/2717480/css-selector-for-first-element-with-class/8539107#8539107
       for details on how this works */
    .message_row.unread {
        .date_row {
            position: relative;
            z-index: 3;
            background-color: hsl(0deg 0% 100%);
        }
    }

    .private-message.unread {
        .date_row {
            background-color: hsl(192deg 20% 95%);
        }
    }

    /* Select all but the first .message_row.unread,
       and remove the properties set from the previous rule. */
    .message_row.unread ~ .message_row.unread {
        .date_row {
            position: unset;
            z-index: 0;
            background-color: transparent;
        }
    }

    .private-message.unread ~ .private-message.unread {
        .date_row {
            background-color: hsl(192deg 20% 95%);
        }
    }
}

.simplebar-content-wrapper {
    /* `simplebar-content-wrapper` has `tabindex=0` set, which makes it focusable
        but we don't want it to have an outline when focused anywhere in the app. */
    outline: none;
}

~~~
#### lightbox.css ####
~~~
#lightbox_overlay {
    background-color: hsl(227deg 40% 16%);

    .image-preview {
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        width: 100%;
        height: calc(100% - 65px - 95px);
        margin: 0;
        overflow: hidden;

        background-size: contain;
        background-repeat: no-repeat;
        background-position: center center;

        & img {
            cursor: move;
            max-height: 100%;
            max-width: 100%;
        }

        .zoom-element {
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
    }

    .exit {
        flex-shrink: 0;

        color: hsl(0deg 0% 100% / 80%);
        font-size: 2rem;
        margin: 6px 20px 0 0;

        transform: scaleY(0.75);
        font-weight: 300;

        opacity: 0;
        pointer-events: none;
        cursor: pointer;
        transition: all 0.2s ease;
    }

    &.show .exit {
        pointer-events: auto;
        opacity: 1;
    }

    .image-info-wrapper {
        background-color: transparent;
        display: flex;
        flex-flow: row wrap;
    }

    .image-description,
    .image-actions {
        margin: 20px;
    }

    .image-actions {
        flex-shrink: 0;
        margin-left: auto;

        .button {
            font-size: 0.9rem;
            min-width: inherit;
            padding: 4px 10px;
            border: 1px solid hsl(0deg 0% 100% / 60%);
            background-color: transparent;
            color: hsl(0deg 0% 100%);
            border-radius: 4px;
            text-decoration: none;
            display: inline-block;
            margin: 0 5px;

            &:hover {
                background-color: hsl(0deg 0% 100%);
                border-color: hsl(0deg 0% 100%);
                color: hsl(227deg 40% 16%);
            }
        }

        .disabled {
            opacity: 0.7;
            cursor: default;

            &:hover {
                background-color: transparent;
                color: hsl(0deg 0% 100%);
                border: 1px solid hsl(0deg 0% 100% / 60%);
            }
        }
    }

    .image-description {
        display: flex;
        flex-direction: column;
        max-width: calc(100% - 400px);
        /* add some extra margin top and remove some bottom to keep the
        height the same. and vertically center the text with the buttons. */
        margin-top: 25px;
        margin-bottom: 15px;

        font-size: 1.1rem;
        color: hsl(0deg 0% 100%);

        .title {
            vertical-align: top;
            font-weight: 400;
            line-height: normal;

            /* Required for text-overflow */
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .user {
            font-weight: 300;
            line-height: normal;
            text-overflow: ellipsis;
            overflow: hidden;
            white-space: pre;

            &::before {
                margin-right: 5px;
                content: "\2014";
            }
        }
    }

    .player-container {
        height: calc(100% - 65px - 95px);
        display: flex;
        text-align: center;
        justify-content: center;
        align-items: center;

        & iframe {
            /* maintain 16:9 ratio. */
            width: calc((100vh - 65px - 95px) * 16 / 9);
            height: 100%;
            margin: auto;
        }
    }

    .center {
        .arrow {
            display: inline-block;
            vertical-align: top;
            margin-top: 25px;
            padding: 5px 10px;

            color: hsl(0deg 0% 100%);
            font-size: 1.8em;
            font-weight: 100;

            transform: scaleY(2);
            cursor: pointer;

            opacity: 0.5;
            transition: all 0.3s ease;

            &:hover {
                opacity: 1;
            }
        }

        .image-list {
            position: relative;
            display: inline-block;
            padding: 15px 0 12px;
            height: 50px;
            font-size: 0;

            max-width: 40vw;
            overflow: hidden;
            white-space: nowrap;

            .image {
                display: inline-block;
                vertical-align: top;
                width: 50px;
                height: 50px;
                margin: 0 2px;

                background-color: hsl(0deg 0% 94% / 20%);
                opacity: 0.5;

                background-size: cover;
                background-position: center;
                cursor: pointer;

                &.selected {
                    opacity: 1;
                }
            }
        }
    }
}

@media only screen and ($ms_min <= width < $md_min) {
    #lightbox_overlay {
        .image-actions {
            width: 100%;
            padding-left: 15px;
            margin-top: 0;
        }

        .image-description {
            max-width: calc(100% - 100px);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            margin-bottom: 5px;
        }

        .center .image-list {
            max-width: 80vw;
        }

        .player-container iframe {
            /* maintain 16:9 ratio. */
            width: 100%;
            height: calc((100vw) * 9 / 16);
            margin: auto;
        }

        .image-preview {
            height: calc(100% - 101px - 104px);
        }

        .image-info-wrapper {
            align-items: flex-end;
        }

        .exit {
            position: absolute;
            right: 5px;
            top: 6px;
        }
    }
}

~~~
#### search.css ####
~~~
#searchbox,
#searchbox_legacy {
    width: 100%;
    height: var(--header-height);

    .navbar-search:not(.expanded) {
        display: none;
    }

    .navbar-search.expanded {
        float: left;
        overflow: hidden;
        margin-top: 0;
        margin-bottom: 0;
        width: calc(100% - 2px);
        position: absolute;

        @media (width < $xl_min) {
            width: calc(100% - 84px);
        }

        @media (width < $md_min) {
            /* todo: Figure out why this has to be different
               from top-navbar-border at this width and resolve it */
            width: calc(100% - 123px);
        }

        .search_close_button {
            display: inline;
            margin-right: 5px;
        }

        .zulip-icon-close {
            font-size: 15px;
        }
    }

    .input-append {
        position: relative;
        width: 100%;
        width: max-content;
        min-width: 100%;

        .zulip-icon-search {
            padding: 0;
            font-size: 20px;
            position: absolute;
            left: 10px;
            top: 10px;
            z-index: 5;

            @media (width < $sm_min) {
                top: 5px;
            }
        }

        .zulip-icon-search:not(.deactivated) {
            cursor: pointer;
        }
    }

    #search_query {
        width: 100%;
        font-size: 16px;
        height: var(--header-height);
        padding: 0;
        padding-left: 5px;
        padding-right: 40px;
        border: none;
        border-radius: 0;
        font-family: "Source Sans 3", sans-serif;
        font-weight: 300;
        line-height: var(--header-height);
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;

        @media (width < $sm_min) {
            vertical-align: text-bottom;
        }
    }

    #search_arrows:focus {
        box-shadow: inset 0 0 0 2px hsl(204deg 20% 74%);
    }

    .search_close_button,
    .search_close_button:disabled:hover {
        position: absolute;
        right: 35px;
        top: 6px;
        background: none;
        border-radius: 0;
        border: none;
        height: 30px;
        text-align: center;
        padding: 4px;
        color: inherit;
        opacity: 0.5;
        font-size: 18px;
        box-shadow: none;
        text-shadow: none;
        z-index: 5;
    }

    .search_close_button {
        &:hover {
            opacity: 1;
        }

        &:disabled {
            visibility: hidden;
        }

        @media (width < $sm_min) {
            top: 0;
        }
    }

    .search_icon {
        position: absolute;
        height: 100%;
        text-decoration: none;
        padding: 0 10px;
        font-size: 20px;
        z-index: 5;
        left: 0;
    }

    #search_arrows {
        font-size: 90%;
        letter-spacing: normal;
    }
}

/* in progress: searchbox with pills */
#searchbox {
    #search_arrows {
        padding-left: 35px;
    }

    .pill-container {
        display: flex;
        flex-wrap: nowrap;
        align-items: center;
        border: none;
        padding: 0;
    }

    @media (width >= $sm_min) {
        .pill {
            padding: 2px 0 !important;
            font-size: 14px;
        }
    }

    @media (width < $sm_min) {
        #search_arrows .pill {
            line-height: 20px;

            .exit {
                top: 0;
            }
        }
    }
}

#searchbox_legacy {
    #search_arrows {
        padding-left: 0;
    }

    #search_query {
        padding-left: 35px;
    }

    .search_close_button {
        right: 0;
    }

    .navbar-search.expanded {
        .search_close_button {
            margin-right: 5px;
        }
    }
}

.typeahead-menu li a {
    .search_list_item {
        display: flex;
        align-items: center;
    }

    .search_list_item .pill-container {
        margin-left: 5px;
    }
}

~~~
#### message_row.css ####
~~~
$avatar_column_width: 46px;
$distance_of_text_elements_from_message_box_top: 8.5px;
$distance_of_non_text_elements_from_message_box_top: 6px;
$sender_name_distance_below_flex_center: 3px;

/* The time column usually just needs enough space to display the
   timestamp. The minimum width here is enough for "22:22 PM", which
   is roughly the widest this will be in English; this is nice as the
   timestamps and message controls will be vertically aligned.

   But in some locales, the time encoding is wider, (especially where
   the "PM" abbreviation is longer), so we allow the column to be
   wider for individual messages if required, to prevent ugly
   line-wrapping. In practice, it's unlikely we'll see anything wider
   than 60px; so the precise value of $time_column_max_width should be
   unimportant. */
$time_column_min_width: 50px; /* + padding */
$time_column_max_width: 150px;

.message_row {
    .messagebox .messagebox-content {
        /* Total 868px
        1    56px   2                                        697px                                                      3     55px     4  60px(min)  5
      1 |‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾|
        |           :   TEXT                                                                                             :   +  ⋮  ☆    :  10:00 AM  |
        |           :   TEXT                                                                                             :              :            |
        |   EDITED  :   TEXT                                                                                             :              :            |
        |           :   TEXT                                                                                             :              :            |
        |           :   TEXT                                                                                             :              :            |
    2,3 |_ _ _ _ _ _:_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ : _ _ _ _ _ _ _:_ _ _ _ _ _ |
        |           :                                                                                                    :              :            |
        |           :                                          [EXPAND / COLLAPSE]                                       :              :            |
      4 |_ _ _ _ _ _:_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ : _ _ _ _ _ _ _:_ _ _ _ _ _ |
        |           :                                                                                                    :              :            |
        |           :                                          [Message Reactions]                                       :              :            |
      5 |___________:____________________________________________________________________________________________________:______________:____________|
        */
        display: grid;
        align-items: start;
        padding-left: 10px;
        grid-template-rows: repeat(4, auto);

        grid-template-columns: $avatar_column_width auto 55px fit-content(
                $time_column_max_width
            );

        @media (width < $sm_min) {
            grid-template-columns: $avatar_column_width auto max-content fit-content(
                    $time_column_max_width
                );
        }

        .message_controls {
            grid-row-start: 1;
            grid-column-start: 3;
            line-height: 1;
            justify-self: end;
            /* We need to position it from top and not vertically centered since we want it
               to have the same position from top when user is editing the message. */
            position: relative;
            top: $distance_of_non_text_elements_from_message_box_top;
            padding: 0;

            @media (width < $sm_min) {
                padding: 0 4px;

                /* This is intended to target the first message_controls child
                   when there are 3 displayed. 4 = 3 + hidden message_failed element. */
                .message_control_button:nth-last-child(4) {
                    display: none;
                }
            }
        }

        .message_edit_notice {
            grid-row-start: 1;
            position: relative;
            top: $distance_of_text_elements_from_message_box_top;
        }

        .message_time {
            line-height: 1;
            justify-self: end;
            padding-right: 10px;
            min-width: $time_column_min_width;
            text-align: end;
            grid-row-start: 1;
            grid-column-start: 4;
            position: relative;
            top: $distance_of_text_elements_from_message_box_top;

            &.notvisible {
                /* This happens when message failed to send. We don't want to
                   display time but still want it to occupy space. */
                width: 45px !important;
                position: unset !important;
            }
        }

        .message_content {
            grid-row-start: 1;
            grid-column-start: 2;
            padding: 4px 0 1px;
        }

        .message_reactions {
            grid-row-start: 4;
            grid-column-start: 2;
        }

        .message_edit {
            grid-row-start: 2;
            grid-column-start: 2;
        }

        .alert-msg {
            grid-row-start: 1;
            grid-column: 3 / 5;
            margin-top: 4px;
        }

        .message_length_controller {
            grid-row-start: 3;
            grid-column-start: 2;
        }
    }

    &.include-sender {
        /*
        1           2                                                                                                    3              4            5
      1 |‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾|
        |  ((((\\\  : Sender Name  EDITED                                                                                :   +  ⋮  ☆    :  10:00 AM  |
      2 |   9_9 3)) :_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ : _ _ _ _ _ _ _:_ _ _ _ _ _ |
        |   \=  ((  :   TEXT                                                                                             :              :            |
        |           :   TEXT                                                                                             :              :            |
        |           :   TEXT                                                                                             :              :            |
        |           :   TEXT                                                                                             :              :            |
        |           :   TEXT                                                                                             :              :            |
      3 |_ _ _ _ _ _:_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ : _ _ _ _ _ _ _:_ _ _ _ _ _ |
        |           :                                                                                                    :              :            |
        |           :                                          [EXPAND / COLLAPSE]                                       :              :            |
      4 |_ _ _ _ _ _:_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ : _ _ _ _ _ _ _:_ _ _ _ _ _ |
        |           :                                                                                                    :              :            |
        |           :                                          [Message Reactions]                                       :              :            |
      5 |___________:____________________________________________________________________________________________________:______________:____________|
        */
        .messagebox .messagebox-content {
            grid-template-rows: 25px repeat(3, auto);
            padding-top: 2px;

            .message_content {
                padding-top: 0;
                grid-row-start: 2;
            }

            .message_time {
                align-self: center;
                position: unset;
                margin-top: 1px;
            }

            .message_edit_notice {
                align-self: center;
                top: 2px;
            }

            .message_controls {
                align-self: center;
                position: unset;
            }

            .message_sender {
                overflow: hidden;
                text-overflow: ellipsis;
                grid-column: 1 / 3;
                grid-row: 1 / 2;

                .zulip-icon.zulip-icon-bot {
                    align-self: center;
                    padding: $sender_name_distance_below_flex_center 0 0 5px;
                }

                &.is_me_message {
                    /*
                1           2                                                                                                    3              4            5
            1,2 |‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾‾‾:‾‾‾‾‾‾‾‾‾‾‾‾|
                |  ((((\\\  :                                                                                                    :              :            |
                |   9_9 3)) : Sender Name is excited to write this multiline message that goes to the next line and takes the    :   +  ⋮  ☆    :  10:00 AM  |
                |   \=  ((  : edit status with it to the next line. EDITED                                                       :              :            |
              3 |_ _ _ _ _ _:_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ : _ _ _ _ _ _ _:_ _ _ _ _ _ |
                |           :                                                                                                    :              :            |
                |           :                                          [EXPAND / COLLAPSE]                                       :              :            |
              4 |_ _ _ _ _ _:_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ : _ _ _ _ _ _ _:_ _ _ _ _ _ |
                |           :                                                                                                    :              :            |
                |           :                                          [Message Reactions]                                       :              :            |
              5 |___________:____________________________________________________________________________________________________:______________:____________|
                */
                    min-height: $avatar_column_width;
                    grid-row: 1 / 3;
                    display: grid;
                    grid-template-columns: $avatar_column_width auto;
                    grid-template-rows: auto;

                    & ~ .alert-msg,
                    & ~ .message_time,
                    & ~ .message_controls {
                        grid-row: 1 / 3;
                    }

                    .sender-status {
                        display: inline;
                        margin: 0;
                        margin-top: 13px;

                        .message_edit_notice {
                            position: relative;
                            top: -1px;
                        }
                    }
                }

                > span {
                    display: flex;
                }

                .inline_profile_picture {
                    flex-shrink: 0;
                    /* Let user profile picture take extra height without
                       having any affect on height of the container. */
                    position: absolute;
                    margin-top: $distance_of_non_text_elements_from_message_box_top;
                }

                .sender_name {
                    overflow: hidden;
                    text-overflow: ellipsis;
                    white-space: nowrap;
                    /* It is important to use line-height `normal` here since user's name can
                       be in any language and `line-height: 1` doesn't work to accommodate text
                       from start and end vertically in all languages. */
                    line-height: normal;
                    outline: none;
                    margin-top: $sender_name_distance_below_flex_center;

                    .sender_name_padding {
                        /* Add padding to align user name with the content */
                        padding-left: $avatar_column_width;
                    }
                }
            }

            &.content_edit_mode {
                .is_me_message {
                    & ~ .alert-msg,
                    & ~ .message_time,
                    & ~ .message_controls {
                        grid-row: 1 / 2;
                    }
                }
            }
        }
    }

    /* Locally echoed messages. */
    &.local .message_time {
        opacity: 0;
    }
}

~~~
#### portico_signin.css ####
~~~
html {
    min-height: 500px;
}

.flex {
    display: flex;
    padding: 80px 0;
    align-items: center;
    justify-content: center;

    min-height: calc(100vh - 402px);
}

.m-10 {
    margin: 10px;
}

.semi-bold {
    font-weight: 600;
}

.white-box {
    position: relative;
    padding: 30px;
    min-width: 0;

    background-color: hsl(0deg 0% 100%);
    box-shadow: 0 0 4px hsl(0deg 0% 0% / 10%);
    border: 1px solid hsl(0deg 0% 87%);
    border-radius: 4px;
}

.bottom-text {
    text-align: center;
    margin-top: 20px;
    font-weight: 500;
    font-size: 0.9em;

    & a {
        color: hsl(164deg 100% 23%);

        &:hover {
            text-decoration: none;
            color: hsl(156deg 62% 61%);
        }
    }
}

#new-realm-creation {
    .get-started {
        font-size: 2rem;
    }
}

.bottom-text-large {
    text-align: center;
    margin-top: 20px;
    font-weight: 500;
    font-size: 1.2em;

    & a {
        color: hsl(164deg 100% 23%);

        &:hover {
            text-decoration: none;
            color: hsl(156deg 62% 61%);
        }
    }
}

.grey {
    color: hsl(0deg 0% 67%);
}

.find-account-page-container #find_account i {
    font-size: 0.8em;
}

.app-main {
    .login-page-header {
        font-size: 1.5em;
        font-weight: 300;
        margin: 0;
        height: 0;
        transform: translateX(-15px) translateY(-60px);
        text-align: left;
    }

    .login-page-container.dev-login {
        .login-page-header {
            height: auto;
            margin-top: 20px;
            transform: none;
            text-align: center;
        }

        & h2 {
            font-size: 1em;
            font-weight: 400;
        }

        .group {
            display: inline-block;
            vertical-align: top;

            margin: 0 20px;
        }

        & select {
            height: 30px;
            padding: 4px 6px;
            width: 220px;
            font-size: 14px;
            color: hsl(0deg 0% 33%);
            border-radius: 4px;
            border: 1px solid hsl(0deg 0% 80%);
            margin-bottom: 10px;
            cursor: pointer;
            background-color: hsl(0deg 0% 100%);
            font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
        }
    }

    &.forgot-password-container {
        font-weight: 400;
    }

    &.find-account-page-container {
        width: 500px;
        font-weight: 400;
    }

    &.goto-account-page-container {
        width: 500px;
        font-weight: 400;

        .realm-redirect-form {
            text-align: center;

            .inline-block {
                text-align: center;
            }
        }
    }

    &.confirm-continue-page-container {
        width: 400px;
        font-weight: 400;

        .white-box {
            min-width: 365px;
        }

        .form-inline {
            display: inline-block;
        }

        .form-inline .outline {
            border: 2px inset hsl(213deg 23% 25%);
            background-color: hsl(0deg 0% 100%);
            color: hsl(213deg 23% 25%);
            padding: 13px 20px 11px;

            &:hover {
                background-color: hsl(213deg 65% 97%);
            }
        }

        & p {
            font-size: 19px;
        }
    }
}

.login-page-container {
    &.dev-login {
        margin-top: 20px;
        border: none;

        .login-form {
            width: auto;
        }
    }

    .group {
        margin: 0 20px;
        display: inline-block;
    }

    .dev-button {
        color: hsl(170deg 41% 52%);
        border: 1px solid hsl(170deg 41% 52%);
        border-radius: 4px;
        background-color: transparent;
        font-family: inherit;
        font-weight: normal;
        line-height: 20px;
        vertical-align: middle;
        margin: 0;
        width: auto;

        transition: color 0.3s ease, border 0.3s ease;

        &:hover {
            color: hsl(156deg 62% 61%);
            border-color: hsl(156deg 62% 61%);
        }

        &.dev-login-button {
            padding: 8px;
            font-size: 19px;
            min-width: 300px;
        }

        &.dev-create-button {
            padding: 6px 12px;
            margin-bottom: 4px;
            font-size: 15px;
        }
    }
}

.new-style .login-page-container .alert,
.register-page-container .new-style .alert {
    margin: 0;
    text-align: left;
    font-size: 0.7em;
    font-weight: 600;
}

.register-page-container {
    &.closed-realm {
        .right-side {
            display: none;
        }

        .left-side {
            border-right: none;
        }

        .invite-required {
            display: block;

            color: hsl(0deg 0% 67%);
            font-weight: normal;
        }
    }

    .invite-required {
        display: none;
        line-height: 1;

        & i {
            margin-right: 5px;
        }
    }
}

.find-account-page-container h3,
.forgot-password-container h3 {
    margin-top: 0;

    font-weight: 300;
    font-size: 2em;
}

.forgot-password-container {
    width: 503px;

    & h3,
    form {
        margin-bottom: 0;
    }
}

.deactivated-realm-container {
    width: 503px;
}

.header {
    color: hsl(0deg 0% 27%);
    background-color: hsl(0deg 0% 100%);
    position: fixed;
    width: 100%;
    top: 0;

    .top-links a,
    .header-main .logo span {
        color: hsl(0deg 0% 27%);
    }
}

.register-form {
    &.new-style {
        text-align: left;
        color: hsl(0deg 0% 45%);
    }

    #errors {
        font-size: 0.8em;
        font-weight: 400;
        margin-bottom: 20px;
        margin-top: 10px;

        &:empty {
            margin-top: 0;
        }
    }

    & button {
        margin-top: 22px;
    }

    .new-organization-button {
        margin-top: 25px;
    }
}

.account-accept-terms-page {
    #registration,
    #accept_tos_button {
        margin: 0;
    }

    .fakecontrol {
        font-weight: normal;
    }

    .description {
        margin-bottom: 20px;
        font-size: 16px;
        font-weight: 400;
    }

    .center-block {
        max-width: 800px;

        .controls {
            margin-bottom: 5px;
        }
    }

    #accept_tos_button {
        margin-top: 20px;
    }
}

.register-account {
    .terms-of-service .input-group,
    .default-stream-groups .input-group,
    .default-stream-groups p {
        width: 330px;
        margin: 0 auto 10px;
    }

    .terms-of-service .text-error {
        position: relative;
        display: block;
        top: -5px;
        padding: 0;
        height: 0;

        font-size: 0.7em;
        font-weight: 600;
    }
}

.account-creation {
    font-weight: 400;

    .pitch {
        margin-bottom: 0;
    }

    .alert.alert-info {
        padding: 8px 14px;
        text-align: left;

        font-size: 1em;
        line-height: 1.3;
    }

    .white-box p:last-of-type {
        margin-bottom: 0;
    }
}

.relative {
    position: relative;
}

.new-style {
    & button {
        display: inline-block;
        vertical-align: top;
        padding: 13px 22px;

        font-family: "Source Sans 3", sans-serif;

        font-size: 1.2rem;
        font-weight: 400;
        box-sizing: border-box;
        outline: none;
        color: hsl(0deg 0% 100%);
        background-color: hsl(213deg 23% 25%);

        margin: 25px 0 5px;
        height: 50px;

        border: none;
        border-radius: 4px;

        transition: all 0.3s ease;

        &:hover {
            background-color: hsl(213deg 33% 31%);
        }

        &:active {
            background-color: hsl(214deg 28% 16%);
        }

        &:focus {
            outline: 3px solid hsl(213deg 81% 79%);
        }

        &.full-width {
            width: 100%;
        }
    }

    .alert-info {
        font-weight: 400;
    }

    .demo-organization-warning {
        position: relative;
        display: block;
        background-color: hsl(360deg 100% 93%);
        border: 1px solid hsl(0deg 0% 80%);
        border-radius: 4px;
        padding: 10px;
        margin: 10px 0;
        font-size: 1rem;
        font-weight: 500;
        line-height: 1.5;
        color: hsl(0deg 0% 27%);

        & a {
            text-decoration: none;
        }

        &::before {
            display: inline;
            margin-right: 8px;

            font-family: FontAwesome;
            font-weight: 600;
            content: "\f071";
        }
    }

    .alert {
        &:not(.alert-info) {
            padding: 0;
            margin-bottom: 5px;
            font-weight: 600;
            font-size: 0.7em;
            line-height: 1.2;
            background-color: transparent;

            border: none;
            color: hsl(0deg 44% 54%);
        }

        &.alert-error {
            text-align: left;
        }
    }

    .form-inline {
        margin: 0;
    }

    .get-started {
        font-size: 2.5rem;
        text-align: center;
        color: hsl(0deg 0% 40%);
        margin-bottom: 20px;
    }

    .right-side .alert {
        max-width: 328px;
    }

    .input-box {
        position: relative;
        display: inline-block;
        vertical-align: top;

        & input[type="text"],
        input[type="email"],
        input[type="password"],
        textarea,
        select {
            padding: 10px 32px 10px 12px;
            margin: 25px 0 5px;

            font-family: "Source Sans 3", sans-serif;
            font-size: 1.2rem;
            line-height: normal;
            height: auto;

            width: 280px;

            border: 1px solid hsl(0deg 0% 87%);
            box-shadow: none;
            border-radius: 4px;
            background-color: hsl(0deg 0% 100%);
            color: hsl(0deg 0% 33%);

            transition: border 0.3s ease;

            &:focus:invalid {
                box-shadow: none;
                color: hsl(0deg 0% 27%);
            }

            &:focus {
                border: 1px solid hsl(0deg 0% 53%);
            }
        }

        & input[type="email"] {
            margin-bottom: 10px;
        }

        & label {
            position: absolute;
            top: 0;
            left: 0;

            margin-top: 1px;

            transition: all 0.3s ease;
        }

        &.moving-label {
            & input[type="text"]:invalid + label,
            input[type="email"]:invalid + label,
            input[type="password"]:invalid + label {
                transform: translateY(39px) translateX(14px);
                font-size: 1.2rem;
                font-weight: 400;
                color: hsl(0deg 0% 67%);

                pointer-events: none;
            }
        }

        & label,
        input[type="text"]:focus + label,
        input[type="email"]:focus + label,
        input[type="password"]:focus + label,
        select:focus + label,
        input[type="text"]:valid + label,
        input[type="email"]:valid + label,
        input[type="password"]:valid + label,
        select:valid + label {
            left: 0;
            transform: translateY(0) translateX(0);
            pointer-events: auto;

            font-size: 1rem;
            font-weight: 600;
            color: hsl(0deg 0% 27%);
        }

        /* The width of the "Organization name" text box
           right above this one is also 326px. */
        & select {
            width: 326px;
            cursor: pointer;
        }

        & p.text-error {
            display: block;
            padding: 0;

            color: hsl(1.1deg 44.7% 50.4%);
            font-size: 0.7em;
            font-weight: 600;
            text-align: left;
            line-height: 1.2;

            position: relative;
            left: 1px;
        }

        & label.text-error {
            display: block;

            top: 0;
            right: 0;
            text-align: right;
            color: hsl(1.1deg 44.7% 50.4%);
            font-size: 0.7em;
            font-weight: 600;
            padding-left: 0;
        }
    }

    .lead {
        margin: 0;
    }

    .inline-block {
        text-align: left;
    }

    .contact-admin p.invite-hint {
        font-size: 1.3rem;
        margin-top: 0.8rem;
        text-align: center;
    }
}

#login_form {
    .input-box {
        display: block;
    }

    .loader {
        display: none;
        vertical-align: top;
        position: relative;

        height: 30px;
        margin-top: -10px;
        top: 5px;
    }
}

#new-user-email-address-visibility {
    text-align: left;
    font-size: 0.8em;
    line-height: normal;
    margin-left: 2px;

    .change_email_address_visibility {
        cursor: pointer;
    }
}

#change-email-address-visibility-modal {
    font-weight: 400;

    & label {
        font-size: inherit;
    }

    & h1 {
        font-weight: 600;
        font-family: inherit;
    }

    & select {
        margin-bottom: 10px;
        width: auto;
        font-size: 16px;
        font-family: inherit;
    }
}

/* -- /accounts/register/ page -- */
.portico-page {
    .pitch {
        & h1 {
            margin-bottom: 5px;
        }

        & p {
            font-weight: 400;
            color: hsl(0deg 0% 67%);
        }
    }

    .or {
        width: 100%;
        display: block;
        margin: 10px auto;
        color: hsl(0deg 0% 34%);
        font-weight: 600;
        text-align: center;
        position: relative;
        z-index: 1;

        &::before {
            content: " ";

            display: inline-block;
            position: absolute;
            width: calc(100% - 5px);
            top: calc(50% - 2px);
            left: 0;
            z-index: -1;

            border-bottom: 2px solid hsl(0deg 0% 87%);
        }

        & span {
            background-color: hsl(0deg 0% 100%);
            padding: 0 5px;
        }
    }
}

.register-account .pitch,
.account-accept-terms-page .pitch {
    margin-bottom: 5px;
    text-align: center;
}

.split-view {
    .org-header {
        text-align: left;

        .info-box {
            display: inline-block;
            position: relative;
            margin: 20px 0 0 20px;
            width: calc(100% - 125px);

            /* full width minus the avatar + padding + borders */
            text-align: left;
        }
    }

    .left-side {
        width: 500px;
        border-right: 1px solid hsl(0deg 0% 93%);
        position: relative;
        left: -1px;

        .description {
            text-align: left;
            font-weight: normal;

            margin-top: 20px;
            margin-right: 10px;
        }

        + .right-side {
            border-left: 1px solid hsl(0deg 0% 93%);
            /* this is to make sure the borders of the left and right side overlap
               each other. */
            padding-left: 15px;
            margin-left: -5px;
        }
    }

    .right-side .form-inline {
        width: 328px;
    }
}

.split-view .right-side,
.split-view .left-side {
    display: inline-block;
    vertical-align: top;
}

.split-view .org-header .avatar,
.register-page-container .org-header .avatar {
    display: inline-block;
    vertical-align: top;

    width: 100px;
    height: 100px;
}

.info-box {
    .organization-name,
    .organization-path {
        max-width: 100%;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
    }

    .organization-name {
        font-size: 1.5em;
        font-weight: 300;
        line-height: 1.2;
    }

    .organization-path {
        font-weight: 400;
        color: hsl(0deg 0% 47%);
        margin-top: 5px;
    }
}

.confirm-email-change-page .white-box {
    max-width: 500px;
    word-break: break-word;
}

.anonymous_access_form {
    & button {
        /* Avoid excessive space at top of login form */
        margin-top: 0;
    }
}

button.login-social-button {
    width: 328px;
    height: auto;
    /* Using 44px gives us more space between text and icon so that they don't overlap. */
    /* Tested in Russian laguange which has the maximum text. */
    padding-left: 44px;
    line-height: 1;

    background-size: auto 60%;
    background-repeat: no-repeat;
    background-position: 13px 50%;
    background-color: hsl(0deg 0% 100%);
    box-shadow: 0 1px 3px hsl(0deg 0% 0% / 30%), 0 0 5px hsl(0deg 0% 0% / 10%);
    margin-left: 0;
    margin-top: 0;

    color: hsl(0deg 0% 34%);

    &:hover {
        background-color: hsl(0deg 0% 98%);
        box-shadow: 1px 2px 5px hsl(0deg 0% 0% / 20%);
    }

    &:active {
        background-color: hsl(0deg 0% 93%);
        box-shadow: 0 1px 1px hsl(0deg 0% 0% / 30%);
    }
}

button#login_auth_button_gitlab,
button#register_auth_button_gitlab {
    /* GitLab icon size looks a bit inconsistent with others. This fixes it. */
    background-size: auto 90%;
    background-position-x: 3px;
}

.login-page-container .right-side .actions,
.back-to-login-wrapper {
    margin: 20px 0 0;
    text-align: left;
}

.back-to-login-wrapper {
    line-height: 0;

    .back-to-login i {
        position: relative;
        top: 5px;

        font-size: 0.8em;
    }
}

.split-view .actions a,
.back-to-login {
    color: hsl(164deg 100% 23%);
    text-decoration: none;
    font-weight: 600;
    font-size: 0.8em;
    line-height: 1.5;
    vertical-align: top;

    transition: color 0.2s ease;

    &:hover {
        text-decoration: none;
        color: hsl(156deg 62% 61%);
    }
}

#registration,
#new-realm-creation {
    width: auto;
    padding: 0;
    margin: 30px;

    & fieldset {
        margin: 30px;

        .input-box:last-child {
            margin-bottom: 0;
        }
    }

    .info-box {
        margin: 10px 0 0 20px;

        .organization-name {
            max-width: 228px;
        }
    }

    .input-box {
        display: block;
        text-align: center;
        width: 330px;
        margin: 25px auto 10px;
        position: relative;

        &.full-width {
            width: calc(100% - 20px);
        }

        & label {
            position: absolute;
            margin: 0;
            top: 0;
            left: 2px;

            &.static {
                width: 100%;
                text-align: left;
                position: static !important;
                margin-left: 2px;
            }
        }

        &.support-form-field {
            width: 450px;

            & input,
            textarea {
                width: 400px;
                font-size: 1rem;
            }

            & textarea {
                color: hsl(0deg 0% 33%);
                vertical-align: middle;
                background-color: hsl(0deg 0% 100%);

                &:focus {
                    outline: 0;
                }
            }
        }
    }

    & [for="realm_in_root_domain"] {
        font-weight: normal !important;
    }

    .register-button-box {
        text-align: center;
    }

    .register-button {
        margin: 25px auto 30px;
        width: 330px;
        border-radius: 4px;
    }

    .support-submit-button {
        margin-top: 20px;
        margin-bottom: 5px;
        width: 450px;
    }

    .register-button .loader {
        display: none;
        vertical-align: top;
        position: relative;
        height: 30px;
        margin-top: -10px;
        top: 5px;
    }

    #id_team_subdomain.subdomain {
        margin-top: 0;
        text-align: right;
        position: relative;
        padding-right: 10px;

        width: 150px;

        + .realm_subdomain_label {
            top: 15px;
            margin-left: 180px;
            display: inline-block;

            font-weight: normal;
            font-size: inherit;
        }
    }

    #subdomain_section {
        .inline-block {
            width: 100%;
        }

        .or {
            margin-top: 0;
        }
    }

    #id_email,
    #support_from,
    #support_realm,
    .not-editable-realm-field {
        font-weight: normal;
        margin: 2px;
        padding-top: 25px;
        text-align: left;
        overflow-wrap: break-word;
    }

    .help-text {
        width: 100%;
        max-width: none;
        margin: 2px 0;
        text-align: left;
        color: hsl(0deg 0% 47%);
        font-size: 0.9rem;
        font-weight: 400;
        line-height: 1.2;
    }

    .help-inline {
        display: block;
    }

    & legend {
        display: block;
        width: 100%;
        padding: 0;
        margin-bottom: 0;
        font-size: 21px;
        line-height: 40px;
        color: hsl(0deg 0% 0% / 50%);
        border: 0;
        border-bottom: 1px solid hsl(0deg 0% 90%);

        + .input-box {
            margin-top: 20px;
        }

        .edit-realm-details {
            float: right;
            cursor: pointer;
        }
    }

    .center-block .pitch {
        margin-bottom: 0;
    }

    .input-group {
        & label {
            font-size: 1rem;

            &.inline-block {
                margin-top: -1px;
            }

            &.marketing_emails_checkbox {
                text-indent: -24px;
                margin-left: 24px;
            }
        }

        &.radio {
            margin: 0;
            padding: 0;
        }
    }

    .org-url {
        margin-bottom: 5px !important;
    }
}

.static.org-url + #subdomain_section {
    margin-top: 0 !important;

    .or {
        display: none;
    }
}

#profile_info_section {
    #profile_avatar {
        border: 1px solid hsl(0deg 0% 80%);
        border-radius: 8px;
        width: 120px;
        height: 120px;
        margin: 0 auto 10px;
    }

    #profile_full_name {
        font-size: 1.2rem;
        font-weight: 400;
    }
}

#source_realm_select_section {
    position: relative;
    top: 15px;
    margin-bottom: 20px;
    font-size: 22px;
}

.goto-account-page {
    #realm_redirect_subdomain {
        text-align: right;
        position: relative;
        padding-right: 10px;
    }

    #realm_redirect_external_host {
        font-size: 20px;
        top: 13px;
        left: 5px;
        position: relative;
    }

    #realm_redirect_description {
        top: 15px;
        position: relative;
    }

    #enter-realm-button {
        margin-top: 14px;
    }
}

#choose_email {
    flex-direction: column;

    .white-box {
        min-width: 450px;
        padding: 30px 0 50px;
    }

    & form {
        padding: 0;
        margin: 0;

        &.select-email-form:hover {
            background-color: hsl(202deg 56% 91%);
            cursor: pointer;

            & i.fa {
                color: hsl(203deg 63% 76%);
            }
        }
    }

    .choose-email-box {
        padding: 13px 0;
        margin: 0 30px;
        border-bottom: 1px solid hsl(0deg 0% 95%);
        display: flex;
        align-items: center;

        & p {
            margin: 0;
            font-size: 0.8em;

            &:last-child {
                line-height: 1.2em;
            }
        }

        .email {
            font-size: 0.95em;
            font-weight: 500;
        }

        & img,
        i {
            width: 35px;
            height: 35px;
            margin-right: 10px;
            border-radius: 3px;
        }

        & i.fa {
            color: hsl(0deg 0% 67%);
            text-align: center;
            line-height: 38px;

            &::before {
                font-size: 30px;
            }
        }
    }
}

/* -- media queries -- */

@media (width <= 950px) {
    .split-view .left-side {
        width: 400px;
    }
}

@media (width <= 850px) {
    .split-view .left-side {
        width: 350px;
    }
}

@media (width <= 815px) {
    .flex {
        min-height: calc(100vh - 530px);
    }
}

@media (width <= 795px) {
    .register-account #registration {
        padding: 10px;
    }

    .register-page-container,
    .login-page-container {
        width: 400px;
        text-align: center;
    }

    .split-view {
        .org-header {
            .avatar {
                width: 50px;
                height: 50px;
            }

            .info-box {
                margin-top: 0;

                .organization-path {
                    margin-top: 0;
                }
            }
        }

        .left-side,
        .right-side {
            display: block;
            margin: 0 auto !important;
            max-width: 100%;
        }

        .left-side + .right-side {
            border-left: none;
            padding: 0;
            margin: 0 auto;
        }

        .left-side {
            border: none;
            margin-right: 0;
            min-height: 0;
            margin-bottom: 20px;
            width: 324px;

            .description {
                margin: 20px 0;

                & a {
                    color: hsl(200deg 100% 36%);
                }
            }
        }

        .right-side {
            width: 324px;
        }
    }
}

@media (width <= 500px) {
    .new-style .get-started {
        font-size: 1.6em;
    }

    .app-main.register-page-container,
    .app-main.login-page-container,
    .app-main.find-account-page-container,
    .app-main.goto-account-page-container,
    .app-main.forgot-password-container {
        display: inline-block;
        padding: 20px;
        width: calc(100% - 40px);
    }

    .forgot-password-container form {
        .input-box {
            text-align: center;
        }

        & button {
            width: 328px;
        }
    }

    .white-box {
        box-shadow: none;
    }

    .account-creation {
        font-weight: 400;
    }

    .flex {
        /* the header becomes smaller, so comp for that. */
        min-height: calc(100vh - 505px);
    }
}

@media (width <= 400px) {
    .flex {
        min-height: calc(100vh - 560px);
    }
}

.account-creation .white-box .user_email {
    word-break: break-all;
}

@media (width >= 800px) {
    .account-creation .white-box {
        max-width: 800px;
    }
}

~~~
#### recent_topics.css ####
~~~
.recent_topics_container {
    padding: 0;
    border-radius: 4px;
    background-color: hsl(0deg 0% 100%);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    max-height: 100vh;

    #recent_topics_table {
        max-width: 100%;
        padding-top: 12px;
        overflow: hidden !important;
        display: flex;
        flex-direction: column;
        border-style: solid;
        border-color: hsl(0deg 0% 88%);
        border-width: 0 1px;
        border-radius: 0;
        margin-top: 40px;
        /* To make the table span full height
         * when rows don't reach bottom of the
         * window. This makes the border span
         * fully to bottom in that case.
         */
        min-height: 100vw;

        & td {
            vertical-align: middle;
            padding: 3px 8px;
        }

        .recent_topics_focusable {
            display: inline-block;

            & > * {
                outline: 0;
            }

            &:focus-within {
                /* Use the same color as the message feed pointer */
                box-shadow: 0 3px 0 hsl(215deg 47% 50%);
            }
        }

        & a {
            color: hsl(205deg 47% 42%);
            text-decoration: none;

            &:hover {
                color: hsl(214deg 40% 58%);
            }
        }

        .required-text:empty::after {
            content: attr(data-empty);
            display: block;
            font-style: italic;
            color: hsl(0deg 0% 67%);
            position: absolute;
        }

        .fa-check-square-o,
        .fa-square-o {
            padding: 0 2px;
            width: 10px;
        }

        .fa-lock {
            padding-right: 3px;
        }

        .fa-envelope {
            font-size: 0.7rem;
            margin-right: 2px;
            position: relative;
            top: -1px;
            opacity: 0.6;
        }

        .table_fix_head {
            padding: 0 !important;
            /* 100px = space occupied by `recent_topics_filter_buttons`( ~49px)
                     + give user some extra space at the bottom so that last
                       topic row is clearly visible. */
            max-height: calc(100vh - 100px);
        }

        .table_fix_head table {
            /* To keep border properties to the thead th. */
            border-collapse: separate;
            margin-bottom: 100px;
        }

        #recent_topics_filter_buttons {
            margin: 0 10px;
            display: flex;
            /* Search box has no height without this in safari. */
            flex: 0 0 auto;
            flex-wrap: wrap;
            justify-content: flex-start;
        }

        .search_group {
            display: flex;
            flex-grow: 1;
            margin: 0 0 10px;
        }

        #recent_topics_search {
            flex-grow: 1;
            padding-right: 20px;
            white-space: nowrap;
            text-overflow: ellipsis;
            overflow: hidden;
        }

        .clear_search_button {
            /* Overrides app_components.css property. */
            padding-top: 6px !important;
        }

        #recent_topics_search_clear {
            margin-top: -10px !important;
        }

        .btn-recent-filters {
            border-radius: 40px;
            margin: 0 5px 10px 0;

            &:focus {
                background-color: hsl(0deg 0% 80%);
                outline: 0;
            }

            &.fake_disabled_button {
                cursor: not-allowed;
                opacity: 0.5;

                &:hover {
                    background-color: hsl(0deg 0% 100%);
                    border-color: hsl(0deg 0% 80%);
                }
            }
        }

        .btn-recent-selected {
            background-color: hsl(0deg 11% 93%);
        }

        .unread_count {
            /* Focus underline can only occupy the total length of the unread count */
            margin-right: 1px;
            margin-left: 1px;
            align-self: center;
            background-color: hsl(105deg 2% 50%);
        }

        .unread_mention_info:not(:empty) {
            margin-right: -5px;
            /* Match with its font-size. */
            line-height: 14px;
        }

        .unread_hidden {
            visibility: hidden;
        }

        .flex_container_pm {
            /* Flex container to fit in user circle and group icon */
            display: flex;
            justify-content: space-between;

            .tippy-content {
                font-weight: 400;
            }
        }

        .flex_container {
            display: flex;
            align-items: center;
        }

        .flex_container .left_part {
            flex-wrap: wrap;

            .user_status_icon_wrapper {
                display: inline-flex;
                align-items: center;
                flex-direction: row;
            }
        }

        .flex_container .right_part {
            margin-left: auto;
            display: inline-flex;
        }

        .recent_topic_actions {
            /* To add spacing between unread count and mute icon */
            margin-left: 10px;
            display: flex;
            flex-flow: row nowrap;
        }

        .mention_in_unread {
            opacity: 0.7;
        }

        .recent_topic_actions.dummy_action_button {
            visibility: hidden;
        }

        .recent_topic_actions .recent_topics_focusable {
            display: flex;
            align-items: center;
            padding-bottom: 3px;
        }

        .recent_topics_participants {
            display: inline-flex; /* Causes LI items to display in row. */
            list-style-type: none;
            margin: auto; /* Centers vertically / horizontally in flex container. */
            height: 24px;
            padding: 4px;
            border-radius: 6px;
            overflow: hidden;

            /*
                By using the row-reverse layout, the visual ordering will be opposite of
                the DOM ordering. This will allows us to stack the items in the opposite
                direction of the natural stacking order without having to mess with the
                zIndex value. The MAJOR DOWNSIDE is that the HTML itself now reads
                backwards, which super janky.
            */
            flex-direction: row-reverse;
        }

        .recent_topics_participant_item {
            height: 24px;
            margin: 0;
            padding: 0 1.5px;
            position: relative;
            min-width: 24px;
            cursor: pointer;

            .fa-user {
                opacity: 0.7;
            }
        }

        .recent_topics_participant_avatar,
        .recent_topics_participant_overflow {
            border: 0;
            border-radius: 6px;
            color: hsl(0deg 0% 100%);
            display: block;
            height: 24px;
            text-align: center;
            background-color: hsl(0deg 0% 88%);
        }

        .recent_topics_participant_overflow {
            color: hsl(0deg 0% 0%);
            line-height: 24px;
        }

        & tr {
            background-color: hsl(100deg 11% 96%);

            &:hover {
                background-color: hsl(210deg 100% 97%);
            }
        }

        .unread_topic {
            background-color: hsl(0deg 0% 100%);
        }

        .last_msg_time {
            float: left;
            margin-right: 5px;
        }

        & thead th {
            background-color: hsl(0deg 0% 100%);
            color: inherit;
            border-top: 1px solid hsl(0deg 0% 0% / 20%) !important;
            border-bottom: 1px solid hsl(0deg 0% 0% / 20%) !important;
            position: sticky;
            top: 0;
            z-index: 1;

            &.active::after,
            &[data-sort]:hover::after {
                content: " \f0d8";
                white-space: pre;
                display: inline-block;
                position: absolute;
                padding-top: 3px;
                font: normal normal normal 12px/1 FontAwesome;
                font-size: inherit;
            }

            &.active {
                opacity: 1;
                transition: opacity 100ms ease-out;

                &.descend::after {
                    content: " \f0d7";
                }
            }

            &[data-sort]:hover {
                cursor: pointer;
                background-color: hsl(0deg 0% 95%);
                transition: background-color 100ms ease-in-out;

                &:not(.active)::after {
                    opacity: 0.3;
                }
            }
        }

        /* These fixed column widths prevent column widths from being adjusted
           as new messages arrive from the server. */
        .recent_topic_stream {
            width: 25%;
            padding: 8px 0 8px 8px;

            & a {
                word-break: break-word;
                hyphens: auto;
            }
        }

        .recent_topic_name {
            width: 40%;

            & a {
                word-break: break-word;
                /* No hyphes for word break since it caused hyphens to appear before
                   the ellipsis `longText-...` which is not desirable. Ellipsis appears due
                   to the line clamp applied below.
                */
            }

            .line_clamp {
                /* This -webkit-box display property is webkit-specific, but
                   it appears that line clamping works fine for this component
                   on Firefox anyway. */
                /* stylelint-disable-next-line value-no-vendor-prefix */
                display: -webkit-box;
                -webkit-line-clamp: 2;
                -webkit-box-orient: vertical;
                overflow: hidden;
            }
        }

        .recent_topic_users {
            width: 20%;
        }

        .recent_topic_timestamp {
            width: 15%;
        }

        & thead .last_msg_time_header {
            /* The responsive table of bootstrap
               somehow ignores the width of ::after
               element. This ensures it is always visible.
               20px = space occupied by ::after (icon) +
               some extra padding.
            */
            padding-right: 20px;
        }

        @media (width < $md_min) {
            /* Hide participants and last message time
               on smaller screens. This ensures user always
               has a nice UI experience. */
            .recent_topic_users,
            .recent_topic_timestamp,
            thead .participants_header,
            thead .last_msg_time_header {
                display: none;
            }

            .recent_topic_actions {
                margin-right: 5px;
                font-size: 15px;
            }
        }

        .private_conversation_row {
            .recent_topic_stream {
                /* Reduce padding of stream section so that user status
                   icon can have more padding without impacting height of the row */
                padding: 5px 0 5px 8px;
            }

            .pm_status_icon {
                display: flex;
                justify-content: center;
                align-items: center;
                /* Increasing vertical padding any further will increase
                the height of the row. */
                padding: 8px;
                position: relative;
                right: -8px; /* To cancel padding-right */
                /* To accommodate fa-group icon */
                width: 14px;
                height: 14px;

                .fa-group {
                    font-size: 0.8rem;
                    /* color: hsl(105, 2%, 50%); */
                    opacity: 0.6;
                }

                .user_circle {
                    /* Shrink the user activity circle for the recent topics context. */
                    min-width: 7px;
                    height: 7px;
                    float: left;
                    position: unset;
                }
            }
        }
    }

    #recent_topics_bottom_whitespace {
        /* For visual reasons, in a message feed, we require a large
         * bottom_whitespace to make it convenient to display new
         * messages as they come in and prevent occluding the last
         * message with an open compose box. Here, the bottom item
         * is rarely interesting context for a message one is
         * composing, but we do need at least 41px to allow the
         * close-compose-box UI element (including border) to not
         * overlap content. Add some more margin so that user
         * can clearly see the end of the topics.
         */
        height: 120px;

        #recent_topics_loading_messages_indicator,
        .bottom-messages-logo {
            display: block;
            position: absolute;
            top: 200px;
            left: 0;
            right: 0;
            margin: auto;

            .loading_indicator_spinner {
                position: relative;
                top: -7px;
            }
        }
    }

    .stream-privacy .zulip-icon.zulip-icon-globe {
        left: -1px;
    }
}

#recent_topics_view {
    display: none;
    position: relative;
}

~~~
#### hotspots.css ####
~~~
/* icon */
.hotspot-icon {
    position: fixed;
    cursor: pointer;
    z-index: 100;

    .dot {
        width: 25px;
        height: 25px;
        margin: -12.5px 0 0 -12.5px;
        border-radius: 50%;
        position: absolute;
        background-color: hsl(196deg 100% 82% / 30%);
        border: 2px solid hsl(215deg 47% 50%);
        top: 50%;
        left: 50%;
    }

    .pulse {
        width: 25px;
        height: 25px;
        margin: -11.5px 0 0 -11.5px;
        position: absolute;
        top: 50%;
        left: 50%;
        background-color: hsl(0deg 0% 100%);
        border-radius: 50%;
        border: 1px solid hsl(205deg 100% 70%);
        transform: scale(2.2);
        opacity: 0;
        animation: pulsate 5s ease-out 0.375s 5;
    }

    .bounce {
        animation: bounce 5s 5;

        .bounce-icon {
            position: absolute;
            left: -5px;
            bottom: 3px;
            transform: rotate(7deg);
            color: hsl(215deg 47% 50%);
            font-size: 2.75em;
            font-weight: 600;
        }
    }
}

@keyframes pulsate {
    0% {
        transform: scale(1);
        opacity: 0.8;
    }

    30%,
    100% {
        transform: scale(2.2);
        opacity: 0;
    }
}

@keyframes bounce {
    0%,
    15%,
    100% {
        transform: translateY(0);
    }

    7.5% {
        transform: translateY(4px);
    }
}

/* popover */
.hotspot.overlay {
    z-index: 104;
    background-color: hsl(191deg 7% 20% / 15%);

    .hotspot-popover {
        position: fixed;
        width: 250px;
        text-align: left;
        box-shadow: 0 5px 10px hsl(223deg 4% 54% / 20%);
        border: 1px solid hsl(0deg 0% 80%);
        border-radius: 4px;

        /* arrows */
        &::after,
        &::before {
            border: solid transparent;
            content: "";
            height: 0;
            width: 0;
            position: absolute;
            pointer-events: none;
        }

        &::after {
            border-width: 12px;
        }

        &::before {
            border-width: 13px;
        }

        &.arrow-top {
            &::before,
            &::after {
                bottom: 100%;
                right: 50%;
            }

            &::after {
                border-bottom-color: hsl(164deg 44% 47%);
                margin-right: -12px;
            }

            &::before {
                border-bottom-color: hsl(0deg 0% 80%);
                margin-right: -13px;
            }
        }

        &.arrow-left {
            &::before,
            &::after {
                right: 100%;
                top: 50%;
            }

            &::after {
                border-right-color: hsl(0deg 0% 100%);
                margin-top: -12px;
            }

            &::before {
                border-right-color: hsl(0deg 0% 80%);
                margin-top: -13px;
            }
        }

        &.arrow-bottom {
            &::before,
            &::after {
                top: 100%;
                right: 50%;
            }

            &::after {
                border-top-color: hsl(0deg 0% 100%);
                margin-right: -12px;
            }

            &::before {
                border-top-color: hsl(0deg 0% 80%);
                margin-right: -13px;
            }
        }

        &.arrow-right {
            &::before,
            &::after {
                left: 100%;
                top: 50%;
            }

            &::after {
                border-left-color: hsl(0deg 0% 100%);
                margin-top: -12px;
            }

            &::before {
                border-left-color: hsl(0deg 0% 80%);
                margin-top: -13px;
            }
        }
    }

    .hotspot-popover-top {
        padding: 0 15px;
        border-top-left-radius: 4px;
        border-top-right-radius: 4px;
        background-color: hsl(164deg 44% 47%);
    }

    .hotspot-title {
        margin: 0;
        font-size: 1.15em;
        font-weight: 600;
        color: hsl(0deg 0% 100%);
    }

    .hotspot-popover-content {
        background-color: hsl(0deg 0% 100%);
        padding: 15px;
    }

    .hotspot-popover-bottom {
        background-color: hsl(0deg 0% 100%);
        height: 90px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
    }

    .hotspot-img {
        position: absolute;
        bottom: 10px;
        left: 4px;
    }

    .hotspot-confirm {
        position: absolute;
        bottom: 15px;
        right: 15px;
    }
}

.hotspot-img {
    height: 83px;
}

.hotspot-confirm {
    max-width: 125px;
    max-height: 70px;
    border: none;
    font-size: 1.15em;
    font-weight: 600;
    color: hsl(0deg 0% 100%);
    background-color: hsl(164deg 44% 47%);
    border-radius: 4px;
    white-space: normal;
    padding: 7px 20px;
    outline: none;

    &:hover {
        background-color: hsl(164deg 44% 56%);
    }
}

/* individual icon z-indexing */
#hotspot_intro_streams_icon,
#hotspot_intro_topics_icon,
#hotspot_intro_gear_icon {
    z-index: 103;
}

~~~
#### integrations.css ####
~~~
$light-blue-border: hsl(208deg 46% 93%);
$border-green: hsl(170deg 47% 53%);
$hover-green: hsl(170deg 65% 85%);
$text-green: hsl(170deg 72% 32%);
$category-text: hsl(219deg 23% 33%);

.portico-landing.integrations {
    color: hsl(0deg 0% 27%);
    font-weight: normal;

    & h1,
    h2,
    h3 {
        &:hover::after {
            content: none;
        }
    }

    .markdown {
        font-size: 1.1rem;
    }

    .main {
        width: calc(100% - 100px);
        max-width: 1170px;
        margin: 0 auto;
        border-radius: 10px;
        background-color: hsl(0deg 0% 100%);
        visibility: hidden;

        & img {
            box-shadow: none;
            border: none;
        }

        @media (width <= 768px) {
            width: calc(100% - 50px);
            margin: 0 auto;
        }

        @media (width <= 450px) {
            width: 100%;
        }
    }

    .padded-content {
        padding: 50px 0;

        .inner-content {
            min-height: 870px;

            .show {
                opacity: 1;
                pointer-events: all;
            }

            @media (width <= 500px) {
                height: auto;
            }
        }

        @media (width <= 450px) {
            padding: 40px 0;
        }
    }

    & ol li {
        list-style: none;
    }

    & ul li {
        list-style: circle;
    }

    .integration-main-text {
        padding: 0 15px;
    }

    .portico-page-heading {
        font-size: 2.5em;
        font-weight: 300;
        line-height: 1.2;
        text-align: center;
        border-bottom: none;

        & a {
            color: inherit;
        }
    }

    .portico-page-subheading {
        font-weight: 400;
        font-size: 1.1em;
        color: hsl(0deg 0% 67%);
        line-height: 1.2;
        text-align: center;
    }

    #integration-search {
        margin-bottom: 30px;

        .searchbar {
            width: calc(100% - 40px);
            display: flex;
            justify-content: center;
            margin: 30px auto 0;

            .searchbar-reset {
                position: relative;

                & input {
                    box-shadow: 0 0 7px 2px hsl(0deg 0% 0% / 3%);

                    font-size: 1em;
                    font-family: inherit;

                    width: 500px;
                    height: 45px;
                    padding: 0 20px 0 50px;
                    border-radius: 40px;
                    border: 1px solid $light-blue-border;
                    display: block;

                    &:focus {
                        border: 1px solid $border-green;
                    }

                    @media (width <= 768px) {
                        width: 375px;
                        margin: 0 auto;
                    }

                    @media (width <= 550px) {
                        width: calc(100% - 80px);
                    }
                }

                & i.fa-search {
                    position: absolute;
                    left: 20px;
                    top: 13px;
                    font-size: 19px;
                    color: $border-green;
                }

                @media (width <= 768px) {
                    width: 445px;
                }

                @media (width <= 550px) {
                    width: 100%;
                }
            }
        }
    }

    .catalog {
        margin-top: 20px;
        padding: 0 30px;
        min-height: 500px;

        .integration-categories-sidebar {
            float: left;
            width: 200px;
            padding: 0 30px 0 0;
            margin: 0;

            &.sticky {
                position: sticky;
                top: 40px;
                margin: auto;
                height: 490px;
                z-index: 10;
            }

            & h3 {
                font-weight: 400;
                font-size: 1.1em;
                margin: 0;
            }

            & h4 {
                font-weight: 400;
                font-size: 0.95em;
                padding: 6px 10px 3px;
                margin: 3px 0;
                border-radius: 5px;
                transition: all 0.3s ease;
                color: $category-text;

                &.selected,
                &:hover {
                    background-color: $hover-green;
                    color: $text-green;
                    cursor: pointer;
                }
            }

            @media (width <= 906px) {
                display: none;
            }
        }
    }

    .integration-categories-dropdown {
        margin: 30px auto;
        display: none;

        .heading {
            font-weight: 600;
        }

        @media (width <= 906px) {
            /* Change it to `display: block` when enabling catergories. */
            display: none;
            width: 670px;

            & h3,
            h4 {
                font-weight: 400;
                margin: 0;
                padding: 12px 20px;
            }

            .dropdown-toggle {
                cursor: pointer;
                display: flex;
                position: relative;
                padding: 0;
                align-items: center;
                justify-content: space-between;
                margin-left: 25px;
                margin-right: 25px;
                border: 1px solid $light-blue-border;
            }

            & i {
                margin-right: 10px;
                font-size: 24px;
            }

            .dropdown-list {
                display: none;
                cursor: pointer;
                padding: 0;
                margin-left: 25px;
                margin-right: 25px;
            }

            & h3 {
                font-size: 1em;
                text-align: left;
            }

            & h4 {
                border-left: 1px solid $light-blue-border;
                border-right: 1px solid $light-blue-border;
                border-bottom: 1px solid $light-blue-border;
                transition: all 0.3s ease;
                font-size: 0.9em;

                &.selected,
                &:hover {
                    background-color: $hover-green;
                    color: $text-green;
                }
            }
        }

        @media (width <= 830px) {
            width: 666px;
        }

        @media (width <= 786px) {
            width: 509px;
        }

        @media (width <= 768px) {
            width: 666px;
        }

        @media (width <= 686px) {
            width: 509px;
        }

        @media (width <= 578px) {
            width: 351px;
        }

        @media (width <= 357px) {
            width: 299px;
        }
    }

    .integration-lozenges {
        overflow: hidden;
        text-align: left;

        @media (width <= 906px) {
            text-align: center;
        }
    }

    .integration-lozenge {
        display: inline-block;
        vertical-align: top;
        width: 153px;
        height: 200px;
        padding: 0 4px;
        margin: 7px 5px;
        border-radius: 5px;
        border: 1px solid $light-blue-border;
        color: $category-text;
        text-align: center;
        transition: all 0.3s ease;

        &:hover {
            border: 1px solid $border-green;
        }

        &.legacy {
            display: none !important;
        }

        .integration-secondary-line-text {
            margin: 0;
            line-height: 10px;
            font-size: 0.65em;
            font-weight: 400;
        }

        .integration-category,
        .realm-category {
            font-size: 0.85em;
            margin-top: 5px;
            font-weight: 400;
            color: hsl(216deg 23% 13% / 50%);
        }

        &.without-category {
            height: 180px;
        }

        .integration-logo {
            margin: 34px auto 20px;
            height: 60px;
        }

        .fa-plus {
            font-size: 59px;
        }

        .integration-name {
            font-size: 1.2em;
            font-weight: 400;
            margin: 10px 4px 0;

            &.with-secondary {
                font-size: 1.1em;
                margin-top: 4px;
            }
        }

        @media (width <= 830px) {
            width: 134px;
            height: 180px;

            .integration-logo {
                margin: 34px auto 15px;
                height: 45px;
            }

            .fa-plus {
                font-size: 45px;
            }

            .integration-name {
                font-size: 1em;
            }

            .integration-category,
            .realm-category {
                font-size: 0.8em;
            }
        }

        @media (width <= 375px) {
            width: 120px;
        }

        @media (width <= 357px) {
            width: 108px;
            height: 160px;

            &.without-category {
                height: 140px;
            }

            .integration-logo {
                margin: 28px auto 10px;
                height: 45px;
            }

            .integration-name {
                font-size: 0.9em;
            }

            .integration-category,
            .realm-category {
                font-size: 0.77em;
            }
        }
    }

    .integration-request {
        font-size: 1em;
        padding: 10px 0;

        & p {
            padding-bottom: 10px;
        }

        .button {
            padding: 11px 25px;
            margin: 0 auto;
            font-size: 0.9em;
        }
    }

    @media (max-width: 550px) {
        .button {
            display: flex;
            flex-wrap: wrap;
            width: 170px;
            justify-content: center;
        }
    }

    .integration-divider {
        padding: 11px 15px 0;
    }

    /* -- integration instructions -- */

    #integration-instructions-group {
        padding: 0 50px;
        display: none;

        .integration-instruction-block {
            flex-direction: column;

            .integration-lozenge {
                width: 125px;
                height: auto;
                padding: 0 5px 20px;
                margin: 0 21px 20px;
                order: 1;

                .integration-category,
                .realm-category {
                    display: none;
                }

                @media (width <= 768px) {
                    border: none;

                    display: flex !important;
                    justify-content: space-between;
                    height: auto;
                    width: auto;
                    margin: unset;
                    padding: unset;

                    .integration-logo {
                        margin: 0;
                    }

                    .integration-name {
                        font-size: 1.2em !important;
                        margin-left: 20px;
                    }
                }
            }

            .name {
                display: none;
                font-size: 1.4em;
                font-weight: 400;
                margin: 0;
                padding-bottom: 35px;
            }

            .categories {
                order: 2;

                .integration-category,
                .realm-category {
                    font-size: 0.9em;
                    font-weight: 400;
                    padding: 6px 3px;
                    margin: 7px 0;
                    width: 165px;
                    text-align: center;
                    border-radius: 5px;
                    transition: all 0.3s ease;
                    background-color: $light-blue-border;
                    color: $category-text;

                    &:hover {
                        background-color: $hover-green;
                        color: $text-green;
                    }
                }
            }

            #integration-list-link {
                margin-left: 30px;
                order: 3;

                & span {
                    display: inline-block;
                    margin-left: 5px;

                    @media (width >= 768px) {
                        margin-top: 15px;
                    }

                    @media (width <= 768px) {
                        display: none;
                    }
                }

                @media (width <= 768px) {
                    font-size: 22px;
                }
            }

            @media (width <= 768px) {
                flex-direction: row;
                justify-content: space-between;
                align-items: center;
                margin-bottom: 20px;
                padding-bottom: 20px;
                border-bottom: 1px solid $light-blue-border;
            }

            @media (width <= 768px) {
                .name {
                    display: block;
                }

                .categories {
                    display: none;
                }
            }
        }

        .integration-instructions {
            .help-content h3 {
                margin: 20px 0;
            }

            .logos_disclaimer {
                font-size: 14px;
                font-style: italic;
            }

            @media (width >= 768px) {
                width: calc(100% - 200px);
            }

            @media (width <= 768px) {
                margin-left: 0;
            }
        }

        @media (width <= 768px) {
            flex-direction: column;
        }

        @media (width <= 450px) {
            padding: 0 25px;
        }
    }
}

.portico-landing.integrations.communities {
    .main {
        visibility: visible;
        max-width: 900px;
    }

    .portico-page-heading {
        color: hsl(0deg 0% 0%);
        font-size: 44px;
    }

    .portico-page-subheading {
        font-weight: 300;
        color: hsl(0deg 0% 20%);
        max-width: 800px;
        line-height: 150%;
        margin: auto;
    }

    .integration-categories-sidebar h3 {
        color: hsl(0deg 0% 0%);
        font-size: 20px;
        font-weight: 600;
    }

    .catalog {
        margin: 50px auto 0;
        max-width: 700px;
    }

    .eligible_realms {
        display: flex;
        flex-direction: column;

        .eligible_realm {
            display: flex;
            margin-bottom: 20px;
            padding: 5px 10px;
            border: 1px solid transparent;
            border-radius: 4px;

            &:hover {
                border: 1px solid hsl(167deg 34% 56%);
            }

            .eligible_realm_logo {
                display: flex;
                margin-right: 20px;
                width: 60px;
                height: 60px;
            }

            .eligible_realm_details {
                display: flex;
                flex-direction: column;
                justify-content: center;

                .eligible_realm_name {
                    font-weight: 400;
                    font-size: 21px;
                    color: hsl(220.6deg 20% 33.3%);
                    line-height: 23px;
                    margin: 0 0 2px;
                }

                .eligible_realm_description {
                    font-weight: 400;
                    font-size: 15px;
                    color: hsl(220deg 2.7% 56.5%);
                    line-height: 19px;
                    margin: 0;
                    /* For restricting text to only two lines.
                       See https://caniuse.com/?search=display%3A%20-webkit-box for support. */
                    overflow: hidden;
                    display: -webkit-box; /* stylelint-disable-line value-no-vendor-prefix */
                    -webkit-line-clamp: 2;
                    -webkit-box-orient: vertical;
                }
            }
        }

        & hr {
            margin: 10px 0;
        }

        .eligible_realm_end_notice {
            text-align: center;
            font-size: 18px;
        }
    }
}

~~~
#### user_circles.css ####
~~~
$active_color: hsl(106deg 74% 44%);
$idle_color: hsl(29deg 84% 51%);

.user_circle_green,
.user_circle_idle,
.user_circle_empty,
.user_circle_empty_line {
    border-radius: 50%;
    border: 1px solid;
    float: left;
    position: relative;
    top: 5px;
}

.user_circle_green {
    background-color: $active_color;
    border-color: $active_color;
}

.user_circle_idle {
    border-color: $idle_color;
    background: linear-gradient(
        to bottom,
        hsl(0deg 0% 100% / 0%) 50%,
        $idle_color 50%
    );
}

.user_circle_empty {
    background-color: transparent;
    border-color: hsl(0deg 0% 50%);
}

.user_circle_empty_line {
    border-color: hsl(0deg 0% 50%);

    &::after {
        content: "";
        background: hsl(0deg 0% 50%);
        height: 1.5px; /* 1px is too thin, 2px is too thick */
        width: 6px;
        display: block;
        margin: 3.25px auto 0; /* (total height - line height) / 2 = 3.25px */
    }
}

~~~
#### compose.css ####
~~~
#compose_buttons {
    text-align: right;
    display: flex;
    flex-direction: row;
    align-items: center;

    .new_message_button {
        margin-left: 4px;

        .button.small {
            font-size: 1em;
            padding: 3px 10px;
            vertical-align: middle;
        }

        .compose_mobile_button {
            & span {
                font-size: 1.2em !important;
                font-weight: 400;
                line-height: 1em;
            }
        }
    }

    .reply_button_container {
        flex: 1;
        min-width: 0;
        margin-left: 0;

        .compose_reply_button {
            width: 100%;
            text-align: left;
            overflow: hidden;
            white-space: nowrap;
            text-overflow: ellipsis;
        }
    }

    .mobile_button_container {
        @media (width >= $sm_min) {
            display: none;
        }
    }

    .stream_button_container,
    .private_button_container {
        @media (width < $sm_min) {
            display: none;
        }
    }
}

/* Main geometry for this element is in zulip.css */
#compose-content {
    border-top: 1px solid hsl(0deg 0% 0% / 7%);
    transition: background-color 200ms linear;
    padding: 4px 4px 8px;
    border-left: 1px solid hsl(0deg 0% 93%);
    border-right: 1px solid hsl(0deg 0% 93%);
    height: 100%;
    display: flex;
    flex-flow: column;
    box-sizing: border-box;
}

.message_comp {
    display: none;
    padding: 5px 10px 0 5px;
}

.autocomplete_secondary {
    opacity: 0.8;
}

.active .autocomplete_secondary {
    opacity: 1;
}

.narrow_to_compose_recipient_current_view_help {
    margin: 0;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.compose_table {
    height: 100%;
    display: flex;
    flex-flow: column;

    .stream-selection-header-colorblock {
        &.message_header_private_message {
            border-radius: 3px 0 0 3px;
            border-bottom: 0;
            background-color: hsl(0deg 0% 27%);
        }
    }

    .right_part {
        padding: 0;
        display: flex;
        align-items: center;
        flex: 1;

        .fa-angle-right {
            font-size: 0.9em;
            -webkit-text-stroke: 0.05em;
            position: relative;
            margin: 0 5px;
        }

        & a.narrow_to_compose_recipients {
            background: transparent;
            font-size: 18px;
            padding: 1px;
            line-height: 20px;
            opacity: 0.7;
            border: 0;
            margin-left: 3px;
            text-decoration: none;
            color: inherit;

            &:hover {
                opacity: 1;
            }
        }
    }

    .pm_recipient {
        margin-left: 5px;
        display: flex;
        align-items: center;
        width: 100%;
    }

    #private-message .to_text {
        vertical-align: middle;

        font-weight: 600;
    }

    #compose-lock-icon,
    #compose-globe-icon {
        position: relative;
        left: 6px;
        top: 0.5px;
        width: 0;
    }

    #compose-globe-icon {
        left: 4.5px;

        .zulip-icon-globe {
            font-size: 12px;
        }
    }

    .message_header {
        background: none;
        background-color: hsl(0deg 0% 92%);
        border: none;
        border-radius: 0;
        box-shadow: none !important;
    }

    .messagebox {
        box-shadow: none !important;
    }
}

#send_message_form {
    margin: 0;
    height: 100%;

    .messagebox-wrapper {
        flex: 1;
    }

    .messagebox {
        /* normally 5px 14px; pull in the right and bottom a bit */
        cursor: default;
        padding: 0;
        background: none;
        box-shadow: none;
        border: none;
        height: 100%;
        display: flex;
        flex-flow: column;
    }

    .message_content {
        margin-right: 0;
    }
}

#below-compose-content {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin-top: 6px;
    margin-bottom: -2px;

    .compose_bottom_top_container {
        display: flex;
    }

    .compose_bottom_bottom_container {
        display: flex;
        justify-content: space-between;
    }
}

#compose_limit_indicator {
    margin-right: 8px;
    font-size: 12px;
    color: hsl(39deg 100% 50%);
    align-self: center;

    &.over_limit {
        color: hsl(0deg 76% 65%);
        font-weight: bold;
    }
}

#compose {
    position: fixed;
    bottom: 0;
    left: 0;
    z-index: 4;
    width: 100%;

    background-color: hsl(0deg 0% 100%);
}

#compose-container {
    display: flex;
    flex-direction: column;
    width: 100%;
    /* This should match the value for .app-main */
    max-width: 1400px;
    margin: auto;
}

#compose_top {
    display: flex;
    justify-content: space-between;
    padding-bottom: 5px;
}

#compose_top_right {
    display: flex;
    align-items: center;
    margin-bottom: auto;

    & button {
        background: transparent;
        color: inherit;
        font-size: 15px;
        font-weight: normal;
        line-height: 20px;
        opacity: 0.7;
        border: 0;
        padding: 0;
        margin-left: 4px;
        vertical-align: unset;
        text-shadow: none;

        &:hover {
            opacity: 1;
        }
    }
}

.collapse_composebox_button,
#compose_close {
    display: none;
}

.compose_banner {
    margin-bottom: 20px;
    border-radius: 5px;
    border: 1px solid;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 15px;
    line-height: 18px;

    & p {
        margin: 0; /* override bootstrap */
        /* 5px right padding + 10px left-margin of the neighbouring button will match the left padding */
        padding: 12px 5px 12px 15px;
    }

    .banner_content {
        flex-grow: 1;
    }

    .compose_banner_action_button {
        border: none;
        border-radius: 4px;
        padding: 5px 10px;
        font-weight: 600;
        margin-left: 10px;
        margin-top: 4.5px;
        margin-bottom: 4.5px;
        height: 32px;
        white-space: nowrap;

        /* Extra margin to ensure the layout is identical when there is no
           close button. */
        &.right_edge {
            margin-right: 10px;
        }
    }

    .compose_banner_close_button {
        font-size: 17px;
        text-decoration: none;
        padding: 12px 10px;
    }

    &.success {
        background-color: hsl(147deg 43% 92%);
        border: 1px solid hsl(147deg 57% 25% / 40%);
        color: hsl(147deg 57% 25%);

        .compose_banner_close_button {
            color: hsl(147deg 57% 25% / 50%);

            &:hover {
                color: hsl(147deg 57% 25%);
            }

            &:active {
                color: hsl(147deg 57% 25% / 75%);
            }
        }
    }

    &.warning {
        background-color: hsl(50deg 75% 92%);
        border-color: hsl(38deg 44% 27% / 40%);
        color: hsl(38deg 44% 27%);

        .compose_banner_close_button {
            color: hsl(38deg 44% 27% / 50%);

            &:hover {
                color: hsl(38deg 44% 27%);
            }

            &:active {
                color: hsl(38deg 44% 27% / 75%);
            }
        }

        .compose_banner_action_button {
            background-color: hsl(38deg 44% 27% / 10%);
            color: inherit;

            &:hover {
                background-color: hsl(38deg 44% 27% / 12%);
            }

            &:active {
                background-color: hsl(38deg 44% 27% / 15%);
            }
        }
    }

    &.error {
        background-color: hsl(4deg 35% 90%);
        border-color: hsl(3deg 57% 33% / 40%);
        color: hsl(4deg 58% 33%);

        .compose_banner_close_button {
            color: hsl(4deg 58% 33% / 50%);

            &:hover {
                color: hsl(4deg 58% 33%);
            }

            &:active {
                color: hsl(4deg 58% 33% / 75%);
            }
        }

        .compose_banner_action_button {
            background-color: hsl(3deg 57% 33% / 10%);
            color: inherit;

            &:hover {
                background-color: hsl(3deg 57% 33% / 12%);
            }

            &:active {
                background-color: hsl(3deg 57% 33% / 15%);
            }
        }
    }

    &.info {
        background-color: hsl(204deg 58% 92%);
        border-color: hsl(204deg 49% 29% / 40%);
        position: relative;
        color: hsl(204deg 49% 29%);

        .compose_banner_close_button {
            color: hsl(204deg 49% 29% / 50%);

            &:hover {
                color: hsl(204deg 49% 29%);
            }

            &:active {
                color: hsl(204deg 49% 29% / 75%);
            }
        }
    }
}

.upload_banner {
    overflow: hidden;

    &.hidden {
        display: none;
    }

    .moving_bar {
        position: absolute;
        width: 0;
        /* The progress updates seem to come every second or so,
        so this is the smoothest it can probably get. */
        transition: width 1s ease-in-out;
        background: hsl(204deg 63% 85%);
        top: 0;
        bottom: 0;
    }

    .upload_msg,
    .compose_banner_close_button {
        z-index: 1;
        position: relative;
    }
}

.composition-area {
    position: relative;
    flex: 1;
}

@keyframes message-limit-flash {
    0% {
        box-shadow: none;
    }

    100% {
        box-shadow: 0 0 0 1pt hsl(0deg 76% 65%);
    }
}

textarea.new_message_textarea {
    display: table-cell;
    width: calc(100% - 12px);
    padding: 5px;
    height: 1.5em;
    max-height: 22em;
    margin-bottom: 0;
    resize: vertical !important;
    margin-top: 5px;
    border-radius: 4px;
    color: hsl(0deg 0% 33%);
    background-color: hsl(0deg 0% 100%);

    &.over_limit,
    &.over_limit:focus {
        box-shadow: 0 0 0 1pt hsl(0deg 76% 65%);

        &.flash {
            animation: message-limit-flash 0.5s ease-in-out infinite;
        }
    }

    &:read-only,
    &:disabled {
        cursor: not-allowed;
        background-color: hsl(0deg 0% 93%);
    }

    &.invalid,
    &.invalid:focus {
        border: 1px solid hsl(3deg 57% 33%);
        box-shadow: 0 0 2px hsl(3deg 57% 33%);
    }
}

textarea.new_message_textarea,
.compose_table .recipient_box {
    border: 1px solid hsl(0deg 0% 0% / 20%);
    box-shadow: none;
    transition: border 0.2s ease;

    &:focus {
        outline: 0;
        border: 1px solid hsl(0deg 0% 67%);
        box-shadow: none;
    }
}

input.recipient_box {
    margin: 0;
    height: 1.1em;
    border-radius: 3px;
}

#stream_message_recipient_stream.recipient_box {
    width: 20%;
    border-radius: 0 3px 3px 0;
    border-left: 0;

    @media (width > $sm_min) {
        min-width: 120px;
    }

    &:focus {
        border-left: none;
    }

    &.lock-padding {
        padding-left: 20px;
    }
}

#stream_message_recipient_topic.recipient_box {
    /* This width roughly corresponds to how long of a topic can appear in
       the left sidebar with a single digit unread count without being
       cut off. */
    width: 175px;
}

#private_message_recipient.recipient_box {
    width: 100%;
}

#compose-send-button {
    height: 24px;
    padding-top: 3px;
    padding-bottom: 3px;
    margin-bottom: 0;
    font-weight: 600;
    font-size: 0.9em;

    .loader {
        display: none;
        position: relative;
        top: -6px;
    }
}

.enter_sends_choices {
    .enter_sends_choice {
        display: flex;
        gap: 8px;
        padding-top: 4px;

        & input[type="radio"] {
            position: relative;
            top: 5px;
            width: auto;
            cursor: pointer;
            margin: 4px 0 0;

            &:focus {
                outline: 1px dotted hsl(0deg 0% 20%);
                outline: 5px auto -webkit-focus-ring-color;
                outline-offset: -2px;
            }
        }

        &:first-child {
            padding: 0 0 4px;
            border-bottom: 1px solid hsl(0deg 0% 0% / 20%);
        }
    }

    .enter_sends_choice_text {
        display: flex;
        flex-direction: column;
    }

    .enter_sends_minor,
    .enter_sends_minor kbd {
        opacity: 0.9;
        font-size: 11px;
        color: hsl(0deg 0% 50%);
    }
}

.enter_sends {
    font-size: 12px;
    height: 14px;
    padding-left: 4px;
    opacity: 0.7;
    margin-bottom: 5px;
    position: relative;
    top: -2px;
    cursor: pointer;

    @media (width < $mm_min) {
        font-size: 11px;
    }

    & kbd {
        height: 16px;
        padding: 0 4px;
    }

    &:hover {
        opacity: 1;
    }

    .enter_sends_true,
    .enter_sends_false {
        display: none;
    }

    & i {
        padding-left: 3px;
        font-size: 12px;
        font-weight: 600;
    }
}

#stream-message,
#private-message {
    display: flex;
}

#private-message {
    align-items: center;
    width: 100%;
}

.tippy-content .compose_control_buttons_container {
    .compose_gif_icon {
        bottom: 5px;
    }
}

.compose_control_buttons_container {
    margin-right: auto;
    display: flex;
    gap: 4px;
    align-items: center;

    .compose_gif_icon {
        font-size: 22px;
        height: 18px;
        line-height: 18px;
    }

    .fa-eye {
        position: relative;
        top: -0.7px;
    }

    .compose_control_menu {
        padding: 0 7px;
        font-size: 15px;
    }

    .compose_control_menu_wrapper {
        opacity: 0.7;
        padding: 0;
        margin: 0;

        &:hover {
            opacity: 1;
        }

        .compose_control_menu {
            opacity: 1;
        }
    }

    .hide-sm,
    .hide-lg {
        display: flex;
        align-items: center;
        gap: 4px;
        padding: 0;
        margin: 0;
    }

    .divider {
        color: hsl(0deg 0% 88%);
        font-size: 20px;
        margin: 0 3px;
    }

    .compose_draft_button {
        font-size: 15px;
        font-weight: 600;
        font-family: "Source Sans 3", sans-serif;
        padding: 0 5px;
        position: relative;
        top: 0.7px;
    }

    .compose_help_button {
        font-size: 20px;
        line-height: 17px;
    }
}

.compose_right_float_container {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    white-space: nowrap;
    gap: 4px;
    margin-top: 2px;
}

a.compose_control_button {
    padding: 5px;
    opacity: 0.7;
    color: inherit;
    text-decoration: none;
    font-size: 17px;
    text-align: center;

    &:hover {
        opacity: 1;
    }
}

/* This is used to override the
 * properties of `a.compose_control_button`
 * without using `!important`.
 */
a.compose_control_button.hide {
    display: none;
}

.drag {
    display: none;
    height: 18px;
    width: 100%;
    top: 23px;
    position: relative;
    cursor: ns-resize;
}

.preview_message_area {
    /* minus 5px padding. */
    width: calc(100% - 12px);
    padding: 5px;
    margin-top: 5px;
    /* the maximum height the textarea gets to. */
    max-height: 308px;
    /* the minimum height the textarea collapses to. */
    min-height: 42px;
    overflow: auto;

    border: 1px solid hsl(0deg 0% 67%);
    border-radius: 4px;
    background-color: hsl(0deg 0% 0% / 2%);
    cursor: not-allowed;
}

.markdown_preview_spinner {
    margin: auto;
}

.dropdown-menu {
    & ul {
        list-style: none;
        margin: 0;
        background: hsl(0deg 0% 100%);
    }

    .typeahead-header {
        margin: 0;
        padding-left: 20px;
        padding-right: 20px;
        padding-top: 4px;
        border-top: 1px solid hsl(0deg 0% 0% / 20%);
        display: flex;
        align-items: center;
    }

    #typeahead-header-text {
        font-size: 12px;
    }

    &.typeahead {
        background: hsl(0deg 0% 100%);
    }
}

.compose_mobile_stream_button i,
.compose_mobile_private_button i {
    margin-right: 4px;
}

@media (width < $xl_min) {
    #compose-content {
        margin-right: 7px;
    }
}

@media (width < $md_min) {
    #compose-content {
        margin-right: 7px;
        margin-left: 7px;
    }
}

@media (width < $mm_min) {
    #stream_message_recipient_topic.recipient_box {
        /* The max-width here is designed to allow this to share space with
           the Stream input in small windows, without leaving empty space. */
        max-width: calc(100% - 90px);
        min-width: 110px;
    }

    #compose-content {
        margin-right: 5px;
        margin-left: 5px;
    }
}

#compose.compose-fullscreen {
    z-index: 99;

    #compose-container {
        height: 100%;
    }

    .message_comp {
        flex: 1;
        display: flex !important;
        flex-flow: column;
    }

    #compose-textarea,
    #preview_message_area {
        /* Setting height to 0 is necessary to make the flex+Simplebar
           combination work correctly, without pushing the compose
           controls offscreen when previewing a very tall message. */
        max-height: none !important;
        height: 0;
        flex: 1;
    }
}

~~~
#### drafts.css ####
~~~
.drafts-container {
    position: relative;
    height: 95%;
    background-color: hsl(0deg 0% 100%);
    border-radius: 4px;
    padding: 0;
    width: 58%;
    overflow: hidden;
    max-width: 1200px;
    max-height: 1000px;
    display: flex;
    flex-direction: column;

    @media (width < $md_min) {
        height: 95%;
        max-width: none;
        width: 90%;
    }

    .drafts-header {
        padding-top: 4px;
        padding-bottom: 8px;
        text-align: center;
        border-bottom: 1px solid hsl(0deg 0% 87%);

        & h1 {
            margin: 0;
            font-size: 1.1em;
            text-transform: uppercase;
        }

        .exit {
            font-weight: 400;
            position: absolute;
            top: 10px;
            right: 10px;
            color: hsl(0deg 0% 67%);
            cursor: pointer;

            .exit-sign {
                position: relative;
                top: 1px;
                margin-left: 3px;
                font-size: 1.5rem;
                line-height: 1;
                font-weight: 600;
                cursor: pointer;
            }
        }
    }

    .drafts-list {
        padding: 10px 25px;
        overflow: auto;

        .no-drafts {
            display: block;
            margin-top: calc(45vh - 30px - 1.5em);
            text-align: center;
            font-size: 1.5em;
            color: hsl(0deg 0% 67%);
            pointer-events: none;
        }

        .removed-drafts {
            display: block;
            text-align: center;
            font-size: 1em;
            color: hsl(0deg 0% 67%);
            pointer-events: none;
        }

        & h2 {
            font-size: 1.1em;
            line-height: normal;
            margin-bottom: 5px;
        }
    }
}

.draft-row {
    padding: 5px 0;

    > div {
        display: inline-block;
        vertical-align: top;
    }

    .draft-info-box {
        width: 100%;
        border: 1px solid hsl(0deg 0% 88%);
        margin-bottom: 10px;

        &.active {
            outline: 2px solid hsl(215deg 47% 50%);
            /* this offset ensures no gap between the blue box and the draft in active state */
            outline-offset: -1px;
        }

        .message_row {
            border: 0;
        }

        .messagebox-content {
            grid-template-rows: auto;
            grid-template-columns: auto max-content;
            padding: 10px;

            .message_content {
                grid-column: 1 / 2;
                /* to space from restore draft button */
                margin-right: 5px;
            }

            .message_top_line {
                grid-column: 2 / 3;
            }
        }

        .messagebox {
            cursor: auto;
            box-shadow: none;
        }

        .draft_controls {
            display: inline-block;
            font-size: 0.9em;

            [data-tippy-root] {
                width: max-content;
                word-wrap: unset;
            }

            .restore-draft {
                cursor: pointer;
                margin-right: 5px;
                color: hsl(170deg 48% 54%);
                opacity: 0.7;

                &:hover {
                    opacity: 1;
                }
            }

            .delete-draft {
                cursor: pointer;
                margin-left: 5px;
                color: hsl(357deg 52% 57%);
                opacity: 0.7;

                &:hover {
                    opacity: 1;
                }
            }
        }
    }
}

~~~
#### pygments.css ####
~~~
.codehilite pre {
    background-color: hsl(0deg 0% 100%);
}

.codehilite .hll {
    background-color: hsl(60deg 100% 90%);
}

.codehilite {
    background-color: hsl(0deg 0% 98%);
}

.codehilite .c {
    color: hsl(180deg 33% 37%);
    font-style: italic;
} /* Comment */
.codehilite .err {
    border: 1px solid hsl(0deg 100% 50%);
} /* Error */
.codehilite .k {
    color: hsl(332deg 70% 38%);
} /* Keyword */
.codehilite .o {
    color: hsl(332deg 70% 38%);
} /* Operator */
.codehilite .cm {
    color: hsl(180deg 33% 37%);
    font-style: italic;
} /* Comment.Multiline */
.codehilite .cp {
    color: hsl(38deg 100% 36%);
} /* Comment.Preproc */
.codehilite .c1 {
    color: hsl(0deg 0% 67%);
    font-style: italic;
} /* Comment.Single */
.codehilite .cs {
    color: hsl(180deg 33% 37%);
    font-style: italic;
} /* Comment.Special */
.codehilite .gd {
    color: hsl(0deg 100% 31%);
} /* Generic.Deleted */
.codehilite .ge {
    font-style: italic;
} /* Generic.Emph */
.codehilite .gr {
    color: hsl(0deg 100% 50%);
} /* Generic.Error */
.codehilite .gh {
    color: hsl(240deg 100% 25%);
    font-weight: bold;
} /* Generic.Heading */
.codehilite .gi {
    color: hsl(120deg 100% 31%);
} /* Generic.Inserted */
.codehilite .go {
    color: hsl(0deg 0% 50%);
} /* Generic.Output */
.codehilite .gp {
    color: hsl(240deg 100% 25%);
    font-weight: bold;
} /* Generic.Prompt */
.codehilite .gs {
    font-weight: bold;
} /* Generic.Strong */
.codehilite .gu {
    color: hsl(300deg 100% 25%);
    font-weight: bold;
} /* Generic.Subheading */
.codehilite .gt {
    color: hsl(221deg 100% 40%);
} /* Generic.Traceback */
.codehilite .kc {
    color: hsl(332deg 70% 38%);
    font-weight: bold;
} /* Keyword.Constant */
.codehilite .kd {
    color: hsl(332deg 70% 38%);
} /* Keyword.Declaration */
.codehilite .kn {
    color: hsl(332deg 70% 38%);
    font-weight: bold;
} /* Keyword.Namespace */
.codehilite .kp {
    color: hsl(332deg 70% 38%);
} /* Keyword.Pseudo */
.codehilite .kr {
    color: hsl(332deg 70% 38%);
    font-weight: bold;
} /* Keyword.Reserved */
.codehilite .kt {
    color: hsl(332deg 70% 38%);
} /* Keyword.Type */
.codehilite .m {
    color: hsl(0deg 0% 40%);
} /* Literal.Number */
.codehilite .s {
    color: hsl(86deg 57% 40%);
} /* Literal.String */
.codehilite .na {
    color: hsl(71deg 55% 36%);
} /* Name.Attribute */
.codehilite .nb {
    color: hsl(195deg 100% 35%);
} /* Name.Builtin */
.codehilite .nc {
    color: hsl(264deg 27% 50%);
    font-weight: bold;
} /* Name.Class */
.codehilite .no {
    color: hsl(0deg 100% 26%);
} /* Name.Constant */
.codehilite .nd {
    color: hsl(276deg 100% 56%);
} /* Name.Decorator */
.codehilite .ni {
    color: hsl(0deg 0% 60%);
    font-weight: bold;
} /* Name.Entity */
.codehilite .ne {
    color: hsl(2deg 62% 52%);
    font-weight: bold;
} /* Name.Exception */
.codehilite .nf {
    color: hsl(264deg 27% 50%);
} /* Name.Function */
.codehilite .nl {
    color: hsl(60deg 100% 31%);
} /* Name.Label */
.codehilite .nn {
    color: hsl(264deg 27% 50%);
    font-weight: bold;
} /* Name.Namespace */
.codehilite .nt {
    color: hsl(120deg 100% 25%);
    font-weight: bold;
} /* Name.Tag */
.codehilite .nv {
    color: hsl(241deg 68% 28%);
} /* Name.Variable */
.codehilite .nx {
    color: hsl(0deg 0% 26%);
} /* Not sure? */
.codehilite .ow {
    color: hsl(276deg 100% 56%);
    font-weight: bold;
} /* Operator.Word */
.codehilite .w {
    color: hsl(0deg 0% 73%);
} /* Text.Whitespace */
.codehilite .mf {
    color: hsl(195deg 100% 35%);
} /* Literal.Number.Float */
.codehilite .mh {
    color: hsl(195deg 100% 35%);
} /* Literal.Number.Hex */
.codehilite .mi {
    color: hsl(195deg 100% 35%);
} /* Literal.Number.Integer */
.codehilite .mo {
    color: hsl(195deg 100% 35%);
} /* Literal.Number.Oct */
.codehilite .sb {
    color: hsl(86deg 57% 40%);
} /* Literal.String.Backtick */
.codehilite .sc {
    color: hsl(86deg 57% 40%);
} /* Literal.String.Char */
.codehilite .sd {
    color: hsl(86deg 57% 40%);
    font-style: italic;
} /* Literal.String.Doc */
.codehilite .s2 {
    color: hsl(225deg 71% 33%);
} /* Literal.String.Double */
.codehilite .se {
    color: hsl(26deg 69% 43%);
    font-weight: bold;
} /* Literal.String.Escape */
.codehilite .sh {
    color: hsl(86deg 57% 40%);
} /* Literal.String.Heredoc */
.codehilite .si {
    color: hsl(336deg 38% 56%);
    font-weight: bold;
} /* Literal.String.Interpol */
.codehilite .sx {
    color: hsl(120deg 100% 25%);
} /* Literal.String.Other */
.codehilite .sr {
    color: hsl(189deg 54% 49%);
} /* Literal.String.Regex */
.codehilite .s1 {
    color: hsl(86deg 57% 40%);
} /* Literal.String.Single */
.codehilite .ss {
    color: hsl(241deg 68% 28%);
} /* Literal.String.Symbol */
.codehilite .bp {
    color: hsl(120deg 100% 25%);
} /* Name.Builtin.Pseudo */
.codehilite .vc {
    color: hsl(241deg 68% 28%);
} /* Name.Variable.Class */
.codehilite .vg {
    color: hsl(241deg 68% 28%);
} /* Name.Variable.Global */
.codehilite .vi {
    color: hsl(241deg 68% 28%);
} /* Name.Variable.Instance */
.codehilite .il {
    color: hsl(0deg 0% 40%);
} /* Literal.Number.Integer.Long */

~~~
#### components.css ####
~~~
/* Reusable, object-oriented CSS base components for all Zulip pages
   (both web app and portico). */

.new-style {
    & label.checkbox {
        padding: 0;
        display: inline-block;
        position: relative;
        vertical-align: top;
        min-height: 20px;

        & input[type="checkbox"] {
            position: absolute;
            clip: rect(0, 0, 0, 0);

            ~ span {
                display: inline-block;
                vertical-align: middle;
                position: relative;
                top: -2px;

                padding: 2px;
                margin: 0 5px 0 0;
                height: 10px;
                width: 10px;

                font-weight: 300;
                line-height: 0.8;
                font-size: 1.3rem;
                text-align: center;
                border: 1px solid hsl(0deg 0% 0% / 60%);

                border-radius: 4px;
                filter: brightness(0.8);

                cursor: pointer;
            }

            &:checked ~ span {
                background-image: url("../images/checkbox.svg");
                background-size: 85%;
                background-position: 50% 50%;
                background-repeat: no-repeat;
            }

            &:disabled ~ span {
                opacity: 0.5;
                cursor: not-allowed;
            }
        }
    }

    & a.no-style {
        color: inherit;
    }
}

a.no-underline,
a.no-underline:hover {
    text-decoration: none;
}

.half-opacity {
    opacity: 0.5;
}

.italic {
    font-style: italic;
}

.simplebar-track {
    .simplebar-scrollbar::before {
        background-color: hsl(0deg 0% 0%);
        box-shadow: 0 0 0 1px hsl(0deg 0% 100% / 33%);
    }

    &.simplebar-vertical {
        transition: width 0.2s ease 1s;

        &.simplebar-hover {
            width: 15px;
            transition: width 0.2s ease;
        }
    }

    &.simplebar-horizontal {
        transition: height 0.2s ease 1s;

        &.simplebar-hover {
            height: 15px;
            transition: height 0.2s ease;
        }
    }
}

i.zulip-icon.zulip-icon-bot {
    color: hsl(180deg 5% 74%);
    vertical-align: top;
    padding: 0 2px;
}

.tippy-content {
    /* Set the default font size for tooltips. Popovers override this with
       a rule looking at the data-theme.
     */
    font-size: 12px;
}

/* Hide the somewhat buggy browser show password feature in IE, Edge,
   since it duplicates our own "show password" widget. */
input::-ms-reveal {
    display: none;
}

.password-div {
    position: relative;

    .password_visibility_toggle {
        position: absolute;
        right: 10px;
        top: 42px;
        opacity: 0.6;

        &:hover {
            opacity: 1;
        }
    }
}

select.bootstrap-focus-style {
    &:focus {
        outline: 1px dotted hsl(0deg 0% 20%);
        outline: 5px auto -webkit-focus-ring-color;
        outline-offset: -2px;
    }
}

~~~
#### stats.css ####
~~~
body {
    font-family: "Source Sans 3", sans-serif !important;
    background-color: hsl(0deg 0% 98%);
}

p {
    margin-bottom: 0;
}

.app-main {
    padding: 0;
    width: auto;
    max-width: none;
}

.svg-container {
    margin: 20px;
}

.center-charts {
    margin: 30px;
}

.stats-page .alert,
.analytics-page-header {
    text-align: center;
}

.summary-stats {
    vertical-align: top;
    margin: 0 auto;
    padding: 20px;
    border: 2px solid hsl(0deg 0% 93%);
    background-color: hsl(0deg 0% 100%);
    width: 395px;

    & h1 {
        margin-top: 0;
        font-size: 1.5em;
    }
}

.flex-container {
    display: flex;
    flex-flow: wrap;
    justify-content: space-around;
}

.chart-container {
    vertical-align: top;
    margin: 10px 0;
    padding: 20px;
    border: 2px solid hsl(0deg 0% 93%);
    background-color: hsl(0deg 0% 100%);

    & button {
        position: relative;
        z-index: 1;
    }

    & h1 {
        margin-top: 0;
        font-size: 1.5em;
    }

    &:not(.pie-chart) .number-stat {
        position: relative;
        top: -30px;
    }

    .button-container {
        position: relative;
        z-index: 1;
        margin-bottom: 5px;

        > * {
            display: inline-block;
            vertical-align: top;
        }
    }
}

.analytics-page-header {
    margin-left: 10px;
}

.rangeslider-container {
    user-select: none;
}

.rangeselector text {
    font-weight: 400;
}

.pie-chart {
    .number-stat {
        float: left;
        font-size: 0.8em;
        font-weight: 400;
    }
}

.buttons button {
    background-color: hsl(0deg 0% 94%);

    &.selected {
        background-color: hsl(0deg 0% 85%);
    }
}

.button {
    font-family: "Source Sans 3", sans-serif !important;
    border: none;
    border-radius: 4px;
    outline: none;
    padding: 2px 6px;

    &:hover {
        background-color: hsl(0deg 0% 84%) !important;
    }
}

.docs_link a {
    font-weight: 300;
    color: inherit;
    text-decoration: none;
}

.tooltip-inner {
    padding: 10px;
    max-width: 350px;

    font-size: 0.75rem;
    font-weight: 400;
    text-align: left;
    line-height: 1.4;
}

.last-update {
    margin: 0 0 30px;

    font-size: 0.8em;
    font-weight: 400;
    text-align: center;
    color: hsl(0deg 0% 67%);
}

#users_hover_humans,
#read_hover_everyone,
#hover_human {
    margin-left: 10px;
}

#id_messages_sent_by_client {
    min-height: 100px;
    width: 750px;
    position: relative;
}

#id_messages_sent_by_message_type {
    height: 300px;
    width: 750px;
    position: relative;
}

#id_messages_sent_over_time,
#id_messages_read_over_time {
    height: 400px;
    width: 750px;
    position: relative;

    &[last_value_is_partial="true"] .points path:last-of-type {
        opacity: 0.5;
    }
}

#id_number_of_users {
    height: 370px;
    width: 750px;
    position: relative;
}

#id_stats_errors {
    display: none;
}

#pie_messages_sent_by_type_total {
    float: right;
}

#users_hover_info,
#read_hover_info,
#hoverinfo {
    display: none;
    font-size: 0.8em;
    font-weight: 400;
    position: relative;
    float: right;
    height: 0;
    top: -25px;
}

.spinner::before {
    content: "";
    box-sizing: border-box;
    position: absolute;
    top: 50%;
    left: 50%;
    width: 30px;
    height: 30px;
    margin-top: -15px;
    margin-left: -15px;
    border-radius: 50%;
    border: 1px solid hsl(0deg 0% 80%);
    border-top-color: hsl(155deg 93% 42%);
    animation: spinner 1s linear infinite;
}

@keyframes spinner {
    to {
        transform: rotate(360deg);
    }
}

~~~
#### left_sidebar.css ####
~~~
/* The width of the empty space in the sidebar to separate
   content from the edge of the window */
$far_left_gutter_size: 10px;
/* This represents the space in the sidebar reserved for symbols like
   the #; labels like the the stream name go to the right of this. */
$left_col_size: 19px;
/* The full topic indentation includes 4px of indent in addition to
   the above (and another 5px of padding not measured here) */
$topic_indent: calc($far_left_gutter_size + $left_col_size + 4px);
$topic_resolve_width: 13px;
/* Space between section in the left sidebar. */
$sections_vertical_gutter: 8px;
$bottom_scrolling_buffer: 25px;
/* space PM / stream / topic names from unread counters / @ mention
indicators by 3px on the right */
$before_unread_count_padding: 3px;

.hashtag {
    &:empty {
        &::after {
            content: "#";
            line-height: 0;
            font-size: 18px;
            font-weight: 800;
        }
    }
}

.stream-privacy {
    font-size: 15px;
    font-weight: 800;
    min-width: $left_col_size;
    text-align: center;

    .zulip-icon.zulip-icon-globe {
        font-size: 12px;
        position: relative;
        top: 1px;
    }
}

/* Ideally we'd handle hashtags using an <i> and just have a single rule here. */
.stream-privacy span.hashtag,
#left-sidebar .filter-icon i {
    padding-right: 3px;

    &.fa-lock {
        position: relative;
        top: 1px;
    }
}

#stream_filters,
#global_filters {
    margin-right: 12px;
}

li.show-more-topics {
    & a {
        font-size: 12px;
        margin-left: $topic_resolve_width;
    }
}

#streams_inline_icon,
.streams_filter_icon {
    float: right;
    opacity: 0.5;
    padding: 3px;
    margin-left: 4px;

    &:hover {
        opacity: 1;
        cursor: pointer;
    }
}

.streams_inline_icon_wrapper {
    float: right;
}

.streams_filter_icon.web_public {
    margin-right: 10px;
}

#streams_inline_icon {
    margin-right: 8px;
}

.tooltip {
    max-width: 18em;
}

#stream_filters {
    overflow: visible;
    margin-bottom: 5px;
    margin-right: 12px;
    padding: 0;
    font-weight: normal;

    .input-append.topic_search_section {
        padding: 2px 0 2px calc($topic_indent - $topic_resolve_width);
        margin-bottom: 3px;
        margin-left: 3px;

        & input {
            width: calc(100% - 50px);
        }
    }

    & li {
        & a:hover {
            text-decoration: none;
        }

        & ul {
            margin-left: 0;

            &.topic-list li {
                padding: 2px 0 2px calc($topic_indent - $topic_resolve_width);

                &.filter-topics {
                    padding-bottom: 0;
                    position: sticky;
                    top: calc($sections_vertical_gutter + 43px);
                    z-index: 2;
                    background-color: hsl(0deg 0% 100%);
                }
            }
        }
    }

    .subscription_block .unread_count {
        margin-right: 15px;
    }

    .subscription_block {
        margin-right: 25px;
        margin-left: $far_left_gutter_size;
        display: flex;
        align-items: center;
        white-space: nowrap;

        &.stream-with-count {
            margin-right: 15px;
        }
    }

    .inactive_stream:not(.active-filter) {
        opacity: 0.5;
    }

    .toggle_stream_mute {
        margin-right: 3px;
        opacity: 0.5;

        &:hover {
            opacity: 1;
        }
    }
}

.narrows_panel {
    & li a {
        margin-top: 1px;

        &:hover {
            text-decoration: none;
        }
    }
}

#left_sidebar_scroll_container {
    outline: none;
    overflow-x: hidden;
    overflow-y: auto;
    position: relative;
    z-index: 0;
    width: 100%;
}

.private_messages_container {
    background: hsl(0deg 0% 100%);
    margin-right: 16px;
    margin-left: 6px;
    z-index: 1;

    #toggle_private_messages_section_icon {
        opacity: 0.7;
        margin-left: -15px;
        min-width: 12px;

        &.fa-caret-right {
            position: relative;
            left: 3px;
        }

        &:hover {
            opacity: 1;
        }
    }

    #private_messages_section_header {
        cursor: pointer;
        padding: 0 10px 1px 6px;
        white-space: nowrap;

        #show_all_private_messages {
            right: 0;
            float: right;
            position: absolute;
            opacity: 0.7;
            text-decoration: none;
            color: inherit;
            margin-right: 21px;
            margin-top: 1px;

            &:hover {
                opacity: 1;
            }
        }

        .unread_count {
            margin-right: 16px;
            margin-top: 2px;
        }
    }

    & ul.pm-list {
        list-style-type: none;
        font-weight: 400;
        margin-left: 0;
        margin-bottom: 0;

        & span.fa-group {
            font-size: 90%;
        }

        & li.pm-list-item {
            position: relative;
            padding: 1px 10px 1px 4px;
            margin-left: 2px;

            & a {
                text-decoration: none;
                color: inherit;
            }

            .pm_left_col {
                min-width: $left_col_size;
            }
        }

        & li#show_more_private_messages {
            cursor: pointer;
            padding-right: 26px;
            padding-left: 6px;

            & a {
                font-size: 12px;
            }

            .unread_count {
                margin-top: 2px;
            }
        }
    }
}

.active_private_messages_section {
    #private_messages_section,
    #private_messages_list,
    #hide_more_private_messages {
        background-color: hsl(202deg 56% 91%);
    }

    #private_messages_section {
        border-radius: 4px 4px 0 0;
    }

    #private_messages_list {
        border-radius: 0 0 4px 4px;
    }

    #more_private_messages_sidebar_title {
        font-weight: 600;
    }
}

:not(.active-sub-filter) {
    &.top_left_row:hover,
    &.bottom_left_row:hover,
    &#stream_filters li.highlighted_stream {
        background-color: hsl(120deg 12.3% 71.4% / 38%);
        border-radius: 4px;
    }
}

#login-link-container,
#subscribe-to-more-streams {
    text-decoration: none;
    margin: 5px auto 5.5px 10px;
    margin-bottom: $bottom_scrolling_buffer;

    & i {
        min-width: 19px;
        text-align: center;

        &::before {
            padding-right: 3px;
        }
    }
}

ul.filters {
    list-style-type: none;
    margin-left: 0;

    & a {
        color: inherit;
    }

    & hr {
        margin-top: 10px;
        margin-bottom: 10px;
    }

    & li.muted_topic,
    li.out_of_home_view {
        opacity: 0.5;
    }

    & li.out_of_home_view {
        &:hover {
            opacity: 0.75;
        }

        & li.muted_topic {
            /* If stream is muted, this resets opacity of muted topics in muted
            stream to 1; since opacity is multiplied down through child
            elements, this avoids an unreadably low opacity. */
            opacity: 1;
        }
    }
}

li.active-filter,
li.active-sub-filter {
    font-weight: 600 !important;
    background-color: hsl(202deg 56% 91%);
    position: relative;
    border-radius: 4px;
}

#stream_filters .narrow-filter.active-filter {
    .topic-list .filter-topics,
    > .bottom_left_row {
        background-color: hsl(202deg 56% 91%);
        border-radius: 4px;
    }
}

#global_filters {
    margin-bottom: $sections_vertical_gutter;

    .filter-icon {
        display: inline-block;
        min-width: $left_col_size;
        text-align: center;
    }

    .top_left_row .unread_count {
        margin-right: 20px;
        margin-top: 2px;
        display: none;
    }

    .top_left_starred_messages .unread_count,
    .top_left_drafts .unread_count {
        background-color: inherit;
        color: inherit;
        border: 0.5px solid hsl(105deg 2% 50%);
        /* The border takes up space, so we need to
           subtract 1px from the usual 2px margin-top */
        margin-top: 1px !important;
    }

    & i {
        opacity: 0.7;
    }
}

li.top_left_all_messages,
li.top_left_mentions,
li.top_left_starred_messages,
li.top_left_drafts,
li.top_left_recent_topics {
    position: relative;
    padding-top: 1px;
    padding-bottom: 1px;

    & a {
        display: block;
    }
}

.top_left_row {
    padding-left: $far_left_gutter_size;
    padding-right: 10px;
}

.conversation-partners {
    line-height: 1.25;
}

.top_left_all_messages i.fa-align-left {
    position: relative;
    font-size: 15px;
}

.top_left_mentions i.fa-at,
.top_left_starred_messages i.fa-star {
    font-size: 13px;
}

.topic-box {
    padding-left: 5px;
    margin-right: 30px;
}

.sidebar-topic-check {
    display: flex;
    align-items: center;
    min-width: $topic_resolve_width;
    font-size: 15px;
    height: 20px;
}

.conversation-partners,
.topic-name,
.stream-name {
    flex: auto;
    min-width: 0;
    white-space: nowrap;
    overflow-x: hidden;
    overflow-x: clip;
    text-overflow: ellipsis;
    padding: 1px $before_unread_count_padding 1px 0;
}

.topic-name {
    /* TODO: We should figure out how to remove this without changing the spacing */
    line-height: 1.1;
}

.left_sidebar_menu_icon_visible {
    display: block !important;
}

/*
    All of our left sidebar handlers use absolute
    positioning.  We should fix that.
*/
.all-messages-sidebar-menu-icon,
.stream-sidebar-menu-icon,
.starred-messages-sidebar-menu-icon,
.drafts-sidebar-menu-icon,
.topic-sidebar-menu-icon {
    position: absolute;
    display: none;
    right: 10px;

    & i {
        padding-right: 0.25em;
        display: inline-block;
        width: 13px;
        vertical-align: middle;
    }

    /*
        If you hover directly over the ellipsis itself,
        show it in black.
    */

    &:hover {
        color: hsl(0deg 0% 0%) !important;
    }

    /*
        Hover does not work for touch-based devices like mobile phones.
        Hence the the icons does not appear, making the user unaware of its
        presence on such devices. The following media property displays the
        icon by default for such behaviour.
    */

    @media (hover: none) {
        display: block;
    }
}

/*
    The All messages and stream ellipsis-v (vertical 3 dots) are
    pretty similar.
*/
.all-messages-sidebar-menu-icon,
.starred-messages-sidebar-menu-icon,
.drafts-sidebar-menu-icon,
.stream-sidebar-menu-icon {
    top: 1px;
    right: 0;
    font-size: 1em;
    text-align: center;
    padding: 0 6px;
}

/*
    For topic ellipsis-v(vertical 3 dots) we use a slightly smaller
    font to show they're "lower" in the hierarchy,
    which also affects it positioning.
*/
.topic-sidebar-menu-icon {
    top: 2px;
    right: 0;
    font-size: 0.9em;
    text-align: center;
    padding: 1px 6px 0;
}

/*
    When you hover over list items, we hover
    the relevant ellipsis-v(vertical 3 dots) in light gray.
*/
li.top_left_all_messages:hover .all-messages-sidebar-menu-icon,
li.top_left_starred_messages:hover .starred-messages-sidebar-menu-icon,
li.top_left_drafts:hover .drafts-sidebar-menu-icon,
#stream_filters li:hover .stream-sidebar-menu-icon,
li.topic-list-item:hover .topic-sidebar-menu-icon {
    display: inline;
    cursor: pointer;
    color: hsl(0deg 0% 53%);
}

ul.topic-list {
    list-style-type: none;
    font-weight: normal;
}

li.topic-list-item {
    position: relative;
    padding-right: 5px;
}

.pm-box,
.topic-box {
    display: flex;
    padding-top: 1px;
    cursor: pointer;
    align-items: center;
}

.pm-box {
    margin-right: 16px;
    align-items: center;

    .user_circle {
        min-width: 8px;
        height: 8px;
        margin-top: 0;
        margin-bottom: 0;
        margin-left: 2px;
        position: relative;
        top: 0;
    }
}

.zero-pm-unreads .pm-box,
.zero-topic-unreads .topic-box {
    margin-right: 15px;
}

.zoom-out {
    #topics_header {
        display: none;
    }

    .zoom-out-hide {
        display: none;
    }
}

#topics_header {
    position: sticky;
    top: 0;
    background-color: hsl(0deg 0% 100%);
    z-index: 2;
    margin-right: 10px;
    padding-top: $sections_vertical_gutter;
    color: hsl(0deg 0% 43%);

    .show-all-streams {
        color: inherit;
        text-decoration: none;
        text-transform: uppercase;
        margin-left: calc($far_left_gutter_size + 2px);

        & i {
            margin: 0 6px 0 13px;
            position: relative;
            top: 1px;
        }
    }
}

#streams_header {
    margin-right: 12px;
    cursor: pointer;
    padding: $sections_vertical_gutter 0 3px calc($far_left_gutter_size + 2px);
    position: sticky;
    /* Ideally, 0px should work here, but maybe simplebar is doing something
       that is creating `0.5px` extra gap in zoomed-in windows. */
    top: -0.5px;
    background: hsl(0deg 0% 100%);
    z-index: 1;

    & input {
        padding-right: 20px;
    }
}

.streams_subheader {
    font-size: 0.8em;
    font-weight: normal;
    padding-left: $far_left_gutter_size;
    cursor: pointer;
    text-align: center;
    margin-right: 12px;

    & span {
        display: flex;
        flex-direction: row;
        width: 100%;
        left: 0.5em;
        right: 0.5em;
        opacity: 0.5;
    }

    & span::before,
    span::after {
        content: " ";
        flex: 1 1;
        vertical-align: middle;
        margin: auto;
        border-top: 1px solid hsl(0deg 0% 88%);
        border-bottom: 1px solid hsl(0deg 0% 100%);
    }

    & span::before {
        margin-right: 0.5em;
    }

    & span::after {
        margin-left: 0.5em;
    }
}

.stream-list-filter {
    width: 216px;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
}

.topic-list-filter {
    /* Input width = 100% - 30px right-margin - 6px right-padding */
    /* To keep the right edge of input along with its borders inline with other
       topic items we consider to subtract the space given for right margin of
       other items, and right padding of input element.  */
    width: calc(100% - 36px);
}

.zero_count {
    visibility: hidden;
}

.searching-for-more-topics img {
    height: 16px;
    margin-left: 6px;
}

.zoom-in {
    .narrow-filter > .bottom_left_row {
        position: sticky;
        top: calc($sections_vertical_gutter + 20px);
        z-index: 2;
        padding-bottom: 1px;
        background-color: hsl(0deg 0% 100%);
    }

    #subscribe-to-more-streams,
    .show-more-topics {
        display: none;
    }

    &.private_messages_container ul.pm-list {
        margin-bottom: $bottom_scrolling_buffer;
    }

    #more_private_messages_sidebar_title {
        display: inline;
    }

    #hide_more_private_messages {
        display: block;
        text-decoration: none;
        color: inherit;
        font-size: 12px;

        & span {
            display: block;
            padding: 2px 0 2px 4px;
        }

        &:hover {
            & span {
                background-color: hsl(120deg 12.3% 71.4% / 38%);
                border-radius: 4px;
            }
        }
    }

    .zoom-in-hide {
        display: none;
    }

    .zoom-in-sticky {
        position: sticky;
        top: 0;
        z-index: 1;
        padding: 3px 0 3px $far_left_gutter_size;
    }

    #show_all_private_messages {
        margin-right: 5px !important;
    }
}

~~~
#### activity.css ####
~~~
.activity_head {
    background-color: hsl(208deg 100% 97%);
}

.table td {
    padding-top: 2px;
    padding-bottom: 2px;
    white-space: nowrap;
}

.table-striped {
    & tr.recently_active {
        & td {
            background-color: hsl(120deg 97% 83%);
        }

        &:nth-child(odd) td {
            background-color: hsl(120deg 70% 76%);
        }
    }
}

td.number {
    text-align: right;
}

.summary-table {
    width: auto;
    margin: 0 auto;
}

tr.admin td:first-child {
    font-weight: bold;
    color: hsl(240deg 100% 50%);
    font-size: 110%;
}

.good {
    font-weight: bold;
    color: hsl(120deg 100% 33%);
}

.bad {
    font-weight: bold;
    color: hsl(0deg 100% 39%);
}

.support-query-result {
    background-color: hsl(210deg 100% 97%);
    padding-left: 15px;
    padding-top: 14px;
    border-radius: 7px;
    box-shadow: 0 10px 7px -6px hsl(0deg 2% 45%);

    & select {
        height: 30px;
        width: 220px;
        padding: 4px 6px;
        font-size: 14px;
        color: hsl(0deg 0% 33%);
        border-radius: 4px;
        border: 1px solid hsl(0deg 0% 80%);
        margin-bottom: 10px;
        cursor: pointer;
        background-color: hsl(0deg 0% 100%);
        vertical-align: middle;
        font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;

        &:focus {
            outline: 1px dotted hsl(0deg 0% 20%);
            outline: 5px auto -webkit-focus-ring-color;
            outline-offset: -2px;
        }
    }

    & input {
        width: 206px;
    }
}

.support-realm-icon {
    max-width: 25px;
    position: relative;
    top: -2px;
}

.support-realm-status-form {
    position: relative;
    top: 20px;
}

.support-discount-form {
    position: relative;
    top: -50px;
}

.support-plan-type-form {
    position: relative;
    top: -10px;
}

.sponsorship-pending-form {
    position: relative;
    top: -25px;
}

.current-plan-details {
    position: relative;
    top: -15px;
}

.approve-sponsorship-form {
    position: relative;
    top: -40px;
}

.billing-method-form {
    position: relative;
    top: -30px;
}

.downgrade-plan-form {
    position: relative;
    top: -75px;
}

.downgrade-plan-method-select {
    width: auto;
}

.scrub-realm-form {
    position: relative;
    top: -70px;
}

.support-search-button {
    border-color: hsl(0deg 0% 83%);
    border-radius: 2px;
}

.support-submit-button {
    position: relative;
    top: -3px;
    border-color: hsl(0deg 0% 83%);
    border-radius: 2px;
}

~~~
#### message_edit_history.css ####
~~~
#message-edit-history {
    .message_top_line {
        float: right;
    }

    .date_row > span {
        display: flex;
        align-items: center;
        white-space: nowrap;

        &::before,
        &::after {
            width: 100%;
            margin: 0;
        }
    }

    .message_time {
        position: static;
    }

    .message_author {
        position: relative;
    }

    .author_details {
        display: block;
        font-size: 12px;
        padding: 1px;
        text-align: right;
    }

    .messagebox-content {
        padding: 0 10px;
    }

    .message_edit_history_content {
        .highlight_text_inserted {
            color: hsl(122deg 72% 30%);
            background-color: hsl(120deg 64% 95%);
        }

        .highlight_text_deleted {
            color: hsl(0deg 100% 50%);
            background-color: hsl(7deg 90% 92%);
            text-decoration: line-through;
            word-break: break-all;
        }
    }
}

~~~
#### widgets.css ####
~~~
.widget-choices {
    & ul {
        padding: 3px;
    }

    & li {
        padding: 2px;
        list-style: none;
    }

    & button {
        font-weight: 700;
        color: hsl(240deg 100% 50%);
    }

    .widget-choices-heading {
        font-weight: 600;
    }
}

.todo-widget {
    /* For the box-shadow to be visible on the left */
    .add-task,
    .add-desc {
        font-size: 14px;
        font-weight: 400;
        margin-right: 4px;
    }

    & label.checkbox {
        display: flex; /* Arrange that a multi-line description line wraps properly. */
        position: relative;
        vertical-align: top;

        & input[type="checkbox"] {
            ~ span {
                height: 12px;
                width: 12px;
                border: 2px solid hsl(156deg 28% 70%);

                border-radius: 4px;
                filter: brightness(1);

                cursor: pointer;
            }

            &:checked ~ span {
                background-image: url("../images/checkbox-white.svg");
                background-size: 75%;
                background-position: 50% 50%;
                background-repeat: no-repeat;
                background-color: hsl(156deg 41% 40%);
                border: 2px solid hsl(156deg 41% 40%);
            }

            &:disabled ~ span {
                opacity: 0.5;
                cursor: not-allowed;
            }

            &:hover ~ span {
                border-color: hsl(156deg 30% 50%);
            }

            &:focus ~ span {
                outline-color: hsl(0deg 0% 100% / 0%);
            }
        }
    }
}

.todo-widget,
.poll-widget {
    & h4 {
        font-size: 18px;
        font-weight: 600;

        /* for example in help `?` widget */
        &.reduced-font-size {
            font-size: 16px;
        }
    }

    & li {
        list-style: none;
        margin: 2px 2px 6px 0;
    }

    & ul {
        margin: 0 0 5px;
        padding: 0;
    }

    & input {
        &.poll-question,
        &.poll-option,
        &.add-task,
        &.add-desc {
            width: 206px;
        }
    }
}

.poll-widget {
    .poll-option {
        font-weight: 400;
        font-size: 14px;
    }

    /* For the box-shadow to be visible on the left */
    & input.poll-option {
        margin-right: 4px;
    }

    & span.poll-option {
        font-weight: 600;
        padding-top: 28px;
    }

    .poll-vote {
        /* This is to ensure that even when the list of poll-names overflows,
        the voting button remains clickable and on top of all other containers. */
        position: relative;
        z-index: 1;

        color: hsl(156deg 41% 40%);
        border-color: hsl(156deg 28% 70%);
        border-style: solid;
        font-weight: 600;
        border-radius: 3px;
        margin-right: 4px;
        padding-left: 2px; /* padding for Chromium browsers */
        padding-right: 2px;
        min-width: 25px;
        height: 25px;
        font-size: 13px;
        background-color: hsl(0deg 0% 100%);

        &:hover {
            border-color: hsl(156deg 30% 50%);
        }

        &:focus {
            outline: 0;
            background-color: hsl(156deg 41% 90%);
        }
    }

    .poll-names {
        color: hsl(0deg 0% 45%);
        padding-left: 4px;
        padding-top: 28px;
        font-size: 14px;
    }
}

button {
    &.task {
        height: 20px;
        width: 20px;
        background-color: transparent;
        border-color: hsl(156deg 28% 70%);
        margin-right: 4px;
        border-radius: 3px;

        &:hover {
            border: 1px solid hsl(194deg 60% 40%);
        }
    }

    &.add-task,
    &.poll-option {
        color: hsl(156deg 41% 40%);
        border: 1px solid hsl(156deg 28% 70%);
        width: 100px;
        border-radius: 3px;
        background-color: hsl(0deg 0% 100%);
        padding: 4px;
        padding-left: 14px;
        padding-right: 14px;
        transition: all 0.2s ease;

        &:hover,
        &:focus {
            outline: 0;
            border-color: hsl(156deg 30% 50%);
        }

        &:active {
            border-color: hsl(156deg 30% 40%);
            color: hsl(156deg 44% 43%);
            background-color: hsl(154deg 33% 96%);
        }
    }
}

input,
button {
    &.add-task,
    &.add-desc,
    &.poll-option,
    &.poll-question {
        padding: 4px 6px;
        margin: 2px 0;
    }
}

.widget-error {
    color: hsl(1deg 45% 50%);
    font-size: 12px;
}

.poll-question-check,
.poll-question-remove {
    width: 28px !important;
    height: 28px;
    border-radius: 3px;
    border: 1px solid hsl(0deg 0% 80%);
    background-color: hsl(0deg 0% 100%);

    &:hover {
        border-color: hsl(0deg 0% 60%);
    }
}

.poll-edit-question {
    opacity: 0.4;
    display: inline-block;
    margin-left: 5px;

    &:hover {
        opacity: 1;
    }
}

.poll-question-header {
    display: inline;
}

.current-user-vote {
    background-color: hsl(156deg 10% 90% / 90%);
}

~~~
#### rendered_markdown.css ####
~~~
.rendered_markdown {
    /* The default top/bottom margins for paragraphs are small, to make sure
       they look nice next to blockquotes, lists, etc. */
    & p {
        margin: 3px 0;
    }

    /* The spacing between two paragraphs is significantly larger.  We
       arrange things so that this spacing matches the spacing between
       paragraphs in two consecutive 1-line messages. */
    & p + p {
        margin-top: 10px;
    }

    /* Ensure bulleted lists are nicely centered in 1-line messages */
    & ul {
        margin: 2px 0 5px 20px;
    }

    /* Swap the left and right margins of bullets for Right-To-Left languages */
    &.rtl ul {
        margin-right: 20px;
        margin-left: 0;
    }

    /* Ensure ordered lists are nicely centered in 1-line messages */
    & ol {
        margin: 2px 0 5px 20px;
    }

    /* Swap the left and right margins of ordered list for Right-To-Left languages */
    &.rtl ol {
        margin-right: 8px;
        margin-left: 0;
    }

    /* Reduce top-margin when a paragraph is followed by an ordered or bulleted list */
    & p + ul,
    p + ol {
        margin-top: 0;
    }

    & hr {
        border-bottom: 1px solid hsl(0deg 0% 87%);
        border-top: 1px solid hsl(0deg 0% 87%);
    }

    /* Headings */
    & h1,
    h2,
    h3,
    h4,
    h5,
    h6 {
        font-weight: 600;
        line-height: 1.4;
        margin-top: 15px;
        margin-bottom: 5px;
    }

    /* Headings: Ensure that messages that start with a heading don't have
       a weirdly blank area at the very start of the message. */
    & h1:first-child,
    h2:first-child,
    h3:first-child,
    h4:first-child,
    h5:first-child,
    h6:first-child {
        margin-top: 0;
    }

    /* We use a modest progression of heading sizes to make them stand out
       from normal next but avoid taking up too much space. */
    & h1 {
        font-size: 1.4em;
    }

    & h2 {
        font-size: 1.3em;
    }

    & h3 {
        font-size: 1.2em;
    }

    & h4 {
        font-size: 1.1em;
    }

    & h5 {
        font-size: 1.05em;
    }

    & h6 {
        font-size: 1em;
    }

    /* Formatting for blockquotes */
    & blockquote {
        padding-left: 5px;
        margin-left: 10px;
        margin-top: 5px;
        margin-bottom: 6px;
        border-left-color: hsl(0deg 0% 87%);

        & p {
            line-height: inherit;
            font-size: inherit;
        }
    }

    &.rtl blockquote {
        padding-left: unset;
        padding-right: 5px;
        margin-left: unset;
        margin-right: 10px;
        border-left: unset;
        border-right: 5px solid hsl(0deg 0% 87%);
    }

    /* Formatting for Markdown tables */
    & table {
        padding-right: 10px;
        margin: 5px;
        width: 99%;
        display: block;
        max-width: fit-content;
        overflow-x: auto;
        white-space: nowrap;
    }

    & thead {
        background-color: hsl(0deg 0% 93%);
    }

    & tr {
        display: table-row;
        vertical-align: inherit;
    }

    & tr th {
        border: 1px solid hsl(0deg 0% 80%);
        padding: 4px;
        text-align: left;
    }

    & tr td {
        border: 1px solid hsl(0deg 0% 80%);
        padding: 4px;
    }

    /* Emoji; sized to be easily understood while not overwhelming text. */
    .emoji {
        height: calc(20em / 14);
        width: calc(20em / 14);
    }

    /* Mentions and alert words */
    .user-mention-me :not(.silent) {
        background-color: hsl(112deg 88% 87%);
    }

    .user-group-mention,
    .user-mention {
        border-radius: 3px;
        padding: 0 0.2em;
        box-shadow: 0 0 0 1px hsl(0deg 0% 80%);
        margin-right: 2px;
        margin-left: 2px;
        white-space: nowrap;
        background: linear-gradient(
            to bottom,
            hsl(0deg 0% 0% / 10%) 0%,
            hsl(0deg 0% 0% / 0%) 100%
        );
        display: inline-block;
        margin-bottom: 1px;
    }

    .alert-word {
        background-color: hsl(102deg 85% 57% / 50%);
    }

    /* Timestamps */
    & time {
        background: hsl(0deg 0% 93%);
        border-radius: 3px;
        padding: 0 0.2em;
        box-shadow: 0 0 0 1px hsl(0deg 0% 80%);
        white-space: nowrap;
        margin-left: 2px;
        margin-right: 2px;
        display: inline-block;
        margin-bottom: 1px;
    }

    /* LaTeX styling */
    .katex-display {
        /* KaTeX sometimes overdraws its bounding box by a little, so we
           enlarge its scrolling area by stealing 3px from the margin
           of the enclosing <p>. */
        margin: -3px 0;
        padding: 3px 0;
        overflow: auto hidden;
    }

    .tex-error {
        color: hsl(0deg 0% 50%);
    }

    /* Spoiler styling */
    .spoiler-block {
        border: hsl(0deg 0% 50%) 1px solid;
        padding: 2px 8px 2px 10px;
        border-radius: 10px;
        position: relative;
        top: 1px;
        display: block;
        margin: 5px 0 15px;

        .spoiler-header {
            padding: 5px;
            font-weight: bold;
        }

        .spoiler-content {
            overflow: hidden;
            border-top: hsl(0deg 0% 50%) 0 solid;
            transition: height 0.4s ease-in-out, border-top 0.4s step-end,
                padding 0.4s step-end;
            padding: 0;
            height: 0;

            &.spoiler-content-open {
                border-top: hsl(0deg 0% 50%) 1px solid;
                transition: height 0.4s ease-in-out, border-top 0.4s step-start,
                    padding 0.4s step-start;
                padding: 5px;
                height: auto;
            }
        }

        .spoiler-button {
            float: right;
            width: 25px;
            height: 25px;

            &:hover .spoiler-arrow {
                &::before,
                &::after {
                    background-color: hsl(0deg 0% 50%);
                }
            }
        }

        .spoiler-arrow {
            float: right;
            width: 13px;
            height: 13px;
            position: relative;
            bottom: -5px;
            left: -10px;
            cursor: pointer;
            transition: 0.4s ease;
            margin-top: 2px;
            text-align: left;
            transform: rotate(45deg);

            &::before,
            &::after {
                position: absolute;
                content: "";
                display: inline-block;
                width: 12px;
                height: 3px;
                background-color: hsl(0deg 0% 83%);
                transition: 0.4s ease;
            }

            &::after {
                position: absolute;
                transform: rotate(90deg);
                top: -5px;
                left: 5px;
            }

            &.spoiler-button-open {
                transform: rotate(45deg) translate(-5px, -5px);

                &::before {
                    transform: translate(10px, 0);
                }

                &::after {
                    transform: rotate(90deg) translate(10px, 0);
                }
            }
        }
    }

    /* embedded link previews */
    .message_inline_image_title {
        font-weight: bold;
    }

    .twitter-image,
    .message_inline_image {
        position: relative;
        margin-bottom: 5px;
        margin-right: 5px;

        /* Sizing CSS for inline images requires care, because images load
           asynchronously, and browsers will unfortunately jump your
           scroll position when elements load above the current
           position in the message feed in a way that changes the
           height of elements. (As of March 2022, both Firefox and
           Chrome exhibit this problem, though in Chrome it is pretty
           subtle).

           We prevent this by setting a fixed height for inline
           previews. 100px is chosen because we don't want images to
           overwhelm conversation in message feeds, as it does in chat
           tools that show images at half-screen height or larger.

           If there are several images next to each other, we display
           them in a grid format; the same considerations requires
           that either use a scrollable region or set a fixed width
           for images so that the browser statically knows whether
           it'll need to overflow. We choose fixed width here. */
        height: 100px;
        width: 150px;

        /* Inline image containers also need an inline-block display in order
           to implement the desired grid layout. */
        display: inline-block;

        /* Set a background for the image; the background will be visible for
           messages whose aspect ratio is different from that of this
           container. */
        border: solid 1px transparent;
        transition: background 0.3s ease;
        background: hsl(0deg 0% 0% / 3%);

        &:hover {
            background: hsl(0deg 0% 0% / 15%);
        }

        & a {
            display: block;
            height: 100%;
            width: 100%;
        }
    }

    &.rtl .twitter-image,
    &.rtl .message_inline_image {
        margin-left: unset;
        margin-right: 5px;
    }

    .twitter-tweet {
        border: 1px solid hsl(0deg 0% 87%);
        padding: 0.5em 0.75em;
        margin-bottom: 0.25em;
        word-break: break-word;
        min-height: 48px;
    }

    .twitter-avatar {
        float: left;
        width: 48px;
        height: 48px;
        margin-right: 0.75em;
    }

    .message_inline_ref {
        margin-bottom: 5px;
        margin-left: 5px;
        height: 50px;
        display: block !important;
        border: none !important;
    }

    &.rtl .message_inline_ref {
        margin-left: unset;
        margin-right: 5px;
    }

    .twitter-image img,
    .message_inline_image img,
    .message_inline_ref img {
        /* We use `scale-down` so that images smaller than the container are
           neither scaled up up or cropped to fit. This preserves
           their aspect ratio, which is often helpful. */
        object-fit: scale-down;

        /* We need to explicitly specify the image dimensions to have
           object-fit work; likely because internally object-fit needs
           to know the frame it is targeting, and images don't default
           to container dimensions. */
        height: 100%;
        width: 100%;

        float: left;
        margin-right: 10px;
        border-radius: inherit;
    }

    .message_inline_image img {
        cursor: zoom-in;
    }

    .youtube-video img,
    .vimeo-video img,
    .embed-video img {
        cursor: pointer;
    }

    &.rtl .twitter-image img,
    &.rtl .message_inline_image img,
    &.rtl .message_inline_ref img {
        float: right;
        margin-right: unset;
        margin-left: 10px;
    }

    & li .message_inline_image img {
        float: none;
    }

    .youtube-video .fa-play::before,
    .embed-video .fa-play::before {
        position: absolute;
        margin: var(--margin-top, 32px) 0 0 var(--margin-left, 45px);
        padding: 5px 8px 5px 10px;
        font-size: 12px;
        border-radius: 4px;
        background-color: hsl(0deg 0% 0%);
        color: hsl(0deg 0% 100%);
        opacity: 0.7;
        top: 0;
        left: 0;
    }

    .message_embed {
        display: block;
        position: relative;
        margin: 5px 0;
        border: none;
        border-left: 3px solid hsl(0deg 0% 93%);
        height: 80px;
        padding: 5px;
        z-index: 1;
        text-shadow: hsl(0deg 0% 0% / 1%) 0 0 1px;

        .message_embed_title {
            padding-top: 0;
            /* to remove the spacing that the font has from the top of the container. */
            margin-top: -5px;

            font-size: 1.2em;
            line-height: normal;
        }

        .message_embed_description {
            position: relative;
            max-width: 500px;
            margin-top: 3px;

            /* to put it below the container gradient. */
            z-index: -1;
        }

        .message_embed_image {
            display: inline-block;
            width: 70px;
            height: 70px;
            background-size: cover;
            background-position: center;
        }

        .data-container {
            position: relative;
            padding: 0 5px;
            display: inline-block;
            vertical-align: top;
            max-width: calc(100% - 115px);
            max-height: 80px;
            overflow: hidden;
        }

        .data-container div {
            display: block;
            border: none;
        }

        .data-container::after {
            content: " ";
            position: absolute;
            width: 100%;
            height: 10%;
            bottom: 0;

            background: linear-gradient(
                0deg,
                hsl(0deg 0% 100%),
                transparent 100%
            );
        }
    }

    &.rtl .message_embed {
        border-left: unset;
        border-right: 3px solid hsl(0deg 0% 93%);
    }

    .message_embed > * {
        display: inherit;
        padding: 5px;
        border: none;
    }

    & a {
        color: hsl(200deg 100% 40%);
        text-decoration: none;

        & code {
            color: hsl(200deg 100% 40%);
        }

        &:hover,
        &:focus {
            color: hsl(200deg 100% 25%);
            text-decoration: underline;

            & code {
                color: hsl(200deg 100% 25%);
            }
        }
    }

    & pre {
        direction: ltr;
        /* code block text is a bit smaller than normal text */
        font-size: 0.825em;
        line-height: 1.4;
        white-space: pre;
        overflow-x: auto;
        word-break: break-all;
        word-wrap: normal;
        margin: 5px 0;
        padding: 5px 7px 3px;
        color: hsl(0deg 0% 20%);
        display: block;
        border: 1px solid hsl(0deg 0% 0% / 15%);
        border-radius: 4px;

        &:hover .copy_codeblock,
        &:hover .code_external_link {
            visibility: visible;
        }
    }

    & pre code {
        font-size: inherit;
        padding: 0;
        white-space: inherit;
        overflow-x: scroll;
        color: inherit;
        border: 0;
    }

    & code {
        /* 11.55px when body is the default 14px; this is chosen to be
        slightly above the 11.5px threshold where the height jumps by a
        pixel on most platforms. */
        font-size: 0.825em;
        unicode-bidi: embed;
        direction: ltr;
        color: hsl(0deg 0% 0%);
        white-space: pre-wrap;
        padding: 0 4px;
        background-color: hsl(0deg 0% 100%);
        border: 1px solid hsl(240deg 13% 90%);
        border-radius: 3px;
    }

    /* Style copy-to-clipboard button inside code blocks */
    .copy_codeblock {
        visibility: hidden;
        /* Having absolute positioning here ensures that the element
        doesn't scroll along with the code div in narrow windows */
        position: absolute;
        right: 2px;
        margin-top: -4px;
    }

    .code_external_link {
        visibility: hidden;
        position: absolute;
        right: 23px;
        margin-top: -3px;
        font-size: 17px;
        /* The default icon and on-hover colors are inherited from <a> tag.
        so we set our own to match the copy-to-clipbord icon */
        color: hsl(0deg 0% 47%);

        &:hover {
            color: hsl(200deg 100% 40%);
        }
    }
}

.preview_content .copy_codeblock {
    /* We avoid displaying copy_codeblock button in previews, because it
       feels odd given that you can just copy-paste the code out of
       the "edit" state.  We may change this decision when we add
       menu options for viewing the code in a coding playground. */
    display: none;
}

.informational-overlays .copy_codeblock {
    display: none;
}

.message_edit_history_content .copy_codeblock {
    /*  Copy code block button is hidden in edit history, this is done
        because of issues faced in copying code blocks in edit history
        modal. This may be changed later as we decide upon a proper ux
        for displaying edit-history. */
    display: none;
}

.message_edit_history_content .code_external_link {
    right: 5px;
}

.preview_content .code_external_link {
    right: 12px;
}

@media (width < $sm_min) {
    .rendered_markdown .message_embed {
        height: auto;

        .message_embed_image {
            width: 100%;
            height: 100px;
        }

        .data-container {
            display: block;
            max-width: 100%;
            margin-top: 10px;
        }
    }
}

.codehilite {
    display: block !important;
    border: none !important;
    background: none !important;
}

/* Both the horizontal scrollbar in <pre/> as well as
   vertical scrollbar in the <textarea/> is styled similarly. */
.message_edit_form textarea,
.rendered_markdown pre {
    /* Ensure the horizontal scrollbar is visible on Mac */
    &::-webkit-scrollbar {
        height: 8px;
        width: 10px;
        background-color: hsl(0deg 0% 0% / 5%);
    }

    &::-webkit-scrollbar-thumb {
        background-color: hsl(0deg 0% 0% / 30%);
        border-radius: 20px;
        transition: all 0.2s ease;
    }

    &::-webkit-scrollbar-thumb:hover {
        background-color: hsl(0deg 0% 0% / 60%);
    }
}

/* Search highlight used in both topics and rendered_markdown */
.highlight {
    background-color: hsl(51deg 94% 74%);
}

~~~
#### typing_notifications.css ####
~~~
#typing_notifications {
    display: none;
    margin-left: 10px;
    font-style: italic;
    color: hsl(0deg 0% 53%);
}

#typing_notification_list {
    list-style: none;
    margin: 0;
}

@media (width < $xl_min) {
    #typing_notifications {
        margin-right: 7px;
    }
}

@media (width < $md_min) {
    #typing_notifications {
        margin-right: 7px;
        margin-left: 7px;
    }
}

~~~
#### dark_theme.css ####
~~~
@import url("flatpickr/dist/themes/dark.css");

%dark-theme {
    color-scheme: dark;

    & body {
        color: hsl(236deg 33% 90%);
    }

    .placeholder {
        color: hsl(0deg 0% 55%);
        opacity: 1;
    }

    & textarea::placeholder,
    input::placeholder {
        @extend .placeholder;
    }

    & a:hover {
        color: hsl(200deg 79% 66%);

        & code {
            color: hsl(200deg 79% 66%);
        }
    }

    & ul.filters a:hover {
        color: inherit;
    }

    /************************* MODAL DARK THEME *******************/
    .dialog_cancel_button {
        background-color: hsl(211deg 29% 14%);
        color: hsl(0deg 0% 100%);
        border: 1px solid hsl(0deg 0% 0% / 60%);
    }

    .modal__btn:disabled {
        opacity: 1;
        background-color: hsl(0deg 0% 83% / 50%);
    }

    .modal__content.simplebar-scrollable-y + .modal__footer {
        border-top: 1px solid hsl(0deg 0% 100% / 20%);
    }

    .modal-bg,
    .modal__container {
        background-color: hsl(212deg 28% 18%);
    }

    .modal__close {
        &::before {
            color: hsl(236deg 33% 90%);
        }

        &:hover {
            background: hsl(0deg 0% 91% / 10%);
        }
    }

    .modal-footer {
        box-shadow: inset 0 1px 0 hsl(0deg 0% 0% / 20%);
    }

    .enter_sends,
    .enter_sends_choices {
        color: hsl(236deg 33% 90%);

        & kbd {
            background-color: hsl(211deg 29% 14%);
            border-color: hsl(211deg 29% 14%);
            box-shadow: inset 0 -1px 0 hsl(210deg 5% 34% / 20%);
            text-shadow: none;
            color: hsl(236deg 33% 90%);
        }

        .enter_sends_minor {
            color: hsl(0deg 0% 80%);
        }
    }

    & table.table-striped thead.table-sticky-headers th {
        background-color: hsl(0deg 0% 0%);

        &[data-sort]:hover {
            background-color: hsl(211deg 29% 14%) !important;
        }
    }

    /* Extend the 'light-border' TippyJS theme, which is intended for
       popovers/menus that should use default background colors, to use
       our dark theme colors in Zulip's dark theme.
     */
    .tippy-box[data-theme~="light-border"] {
        .tippy-content a {
            color: hsl(236deg 33% 90%);

            &.compose_control_button:hover {
                color: hsl(200deg 79% 66%);
            }
        }

        &[data-placement^="top"] {
            > .tippy-arrow {
                &::before {
                    border-top-color: hsl(235deg 18% 7%);
                }
            }
        }

        &[data-placement^="bottom"] {
            > .tippy-arrow {
                &::before {
                    border-bottom-color: hsl(235deg 18% 7%);
                }
            }
        }

        &[data-placement^="left"] {
            > .tippy-arrow {
                &::before {
                    border-left-color: hsl(235deg 18% 7%);
                }
            }
        }

        &[data-placement^="right"] {
            > .tippy-arrow {
                &::before {
                    border-right-color: hsl(235deg 18% 7%);
                }
            }
        }
    }

    .tippy-box:not([data-theme]) {
        background: hsl(0deg 0% 0%);

        &[data-placement^="top"] > .tippy-arrow::before {
            border-top-color: hsl(0deg 0% 0%);
        }

        &[data-placement^="bottom"] > .tippy-arrow::before {
            border-bottom-color: hsl(0deg 0% 0%);
        }

        &[data-placement^="left"] > .tippy-arrow::before {
            border-left-color: hsl(0deg 0% 0%);
        }

        &[data-placement^="right"] > .tippy-arrow::before {
            border-right-color: hsl(0deg 0% 0%);
        }
    }

    & body,
    .app-main,
    .header-main,
    .column-middle,
    #compose,
    .column-left .left-sidebar,
    .column-right .right-sidebar,
    #groups_overlay .right,
    #subscription_overlay .right,
    #settings_page .right,
    #streams_header,
    .private_messages_container,
    .message_header,
    .header {
        background-color: hsl(212deg 28% 18%);
    }

    #scroll-to-bottom-button-container {
        background: transparent;

        & span {
            color: hsl(0deg 0% 27%);
        }
    }

    .compose_banner {
        .above_compose_banner_action_link {
            color: hsl(200deg 100% 50%);
        }

        &.success {
            background-color: hsl(147deg 100% 8%);
            border-color: hsl(149deg 48% 52% / 40%);
            color: hsl(147deg 51% 80%);

            .compose_banner_close_button {
                color: hsl(147deg 51% 55% / 50%);

                &:hover {
                    color: hsl(147deg 51% 55%);
                }

                &:active {
                    color: hsl(147deg 51% 55% / 75%);
                }
            }
        }

        &.warning {
            background-color: hsl(53deg 100% 11%);
            border-color: hsl(38deg 44% 60% / 40%);
            color: hsl(50deg 45% 80%);

            .compose_banner_close_button {
                color: hsl(50deg 45% 61% / 50%);

                &:hover {
                    color: hsl(50deg 45% 61%);
                }

                &:active {
                    color: hsl(50deg 45% 61% / 75%);
                }
            }

            .compose_banner_action_button {
                background-color: hsl(50deg 45% 61% / 10%);
                color: hsl(50deg 45% 61%);

                &:hover {
                    background-color: hsl(50deg 45% 61% / 15%);
                }

                &:active {
                    background-color: hsl(50deg 45% 61% / 20%);
                }
            }
        }

        &.error {
            background-color: hsl(0deg 60% 19%);
            border-color: hsl(3deg 73% 74% / 40%);
            color: hsl(3deg 73% 80%);

            .compose_banner_close_button {
                color: hsl(3deg 73% 74% / 50%);

                &:hover {
                    color: hsl(3deg 73% 74%);
                }

                &:active {
                    color: hsl(3deg 73% 74% / 75%);
                }
            }

            .compose_banner_action_button {
                background-color: hsl(3deg 73% 74% / 10%);
                color: hsl(3deg 73% 74%);

                &:hover {
                    background: hsl(3deg 73% 74% / 15%);
                }

                &:active {
                    background: hsl(3deg 73% 74% / 20%);
                }
            }
        }

        &.info {
            background-color: hsl(204deg 100% 12%);
            border-color: hsl(205deg 58% 69% / 40%);
            position: relative;
            color: hsl(205deg 58% 80%);

            .compose_banner_close_button {
                color: hsl(205deg 58% 69% / 50%);

                &:hover {
                    color: hsl(205deg 58% 69%);
                }

                &:active {
                    color: hsl(205deg 58% 69% / 75%);
                }
            }
        }
    }

    .upload_banner {
        .moving_bar {
            background: hsl(204deg 63% 18%);
        }
    }

    & textarea.new_message_textarea {
        &.invalid,
        &.invalid:focus {
            border-color: hsl(3deg 73% 74%);
            box-shadow: 0 0 2px hsl(3deg 73% 74%);
        }
    }

    .message_embed .data-container::after {
        background: linear-gradient(
            0deg,
            hsl(212deg 28% 18%),
            transparent 100%
        );
    }

    .column-left .left-sidebar,
    .stream_name_search_section,
    .group_name_search_section,
    .column-right .right-sidebar {
        border-color: hsl(0deg 0% 0% / 20%);
    }

    .dark .message_label_clickable.stream_label,
    .dark .stream_label,
    .stream_label {
        color: hsl(212deg 28% 18%);
    }

    .new-style label.checkbox input[type="checkbox"] ~ span {
        border-color: hsl(0deg 0% 100% / 40%);
    }

    .streams_popover .sp-container {
        background-color: transparent;

        & button {
            background-color: hsl(208deg 35% 11%);
            border: 1px solid hsl(210deg 36% 4%);
            color: hsl(236deg 31% 90%);
        }

        .sp-picker-container {
            border-left: solid 1px hsl(210deg 36% 4%);
        }
    }

    /* this one is because in the app we have blue and in dark-theme it should be white. */
    .popover a {
        color: inherit;
    }

    .dark_background a,
    a.dark_background:hover,
    .dark_background,
    .message_reactions .message_reaction_count,
    .message_reactions .reaction_button i,
    .message_reactions:hover .message_reaction + .reaction_button {
        color: inherit !important;
    }

    /* It's a little annoying that we need to specify the different
       background colors for these, but this alert feature can't use a
       transparent background without creating other problems */
    .alert-msg {
        background-color: hsl(212deg 28% 18%);
    }

    .private-message .alert-msg {
        background-color: hsl(208deg 17% 29%);
    }

    .active_private_messages_section {
        #private_messages_section,
        #private_messages_list,
        #hide_more_private_messages {
            background-color: hsl(199deg 33% 46% / 20%);
        }
    }

    /* do not turn the .message_header .stream_label text dark on hover because they're
       on a dark background, and don't change the dark labels dark either. */
    .message_header:not(.dark_background)
        a.stream_label:not(.dark_background):hover {
        color: hsl(212deg 28% 18%);
    }

    .message_header {
        box-shadow: 0 -1px 0 0 hsl(212deg 28% 18%);
    }

    /* these are converting grey things to "new grey" */
    :disabled,
    input:not([type="radio"]):read-only,
    textarea:read-only {
        color: inherit;
        opacity: 0.5;
    }

    .sidebar-title {
        color: inherit;
        opacity: 0.75;
    }

    .rendered_markdown button,
    .new-style .button {
        background-color: hsl(0deg 0% 0% / 20%);

        &:not(
                .sea-green,
                .btn-danger,
                .btn-warning,
                .btn-link,
                .poll-vote,
                button.poll-option,
                button.add-task
            ) {
            border-color: hsl(0deg 0% 0% / 60%);
            color: inherit;
        }

        &.btn-link {
            border-color: hsl(0deg 0% 0% / 60%);
            color: hsl(200deg 79% 66%);
        }

        &:hover,
        &:focus,
        &:active {
            background-color: hsl(0deg 0% 0% / 15%);
        }
    }

    .rendered_markdown .message_inline_image {
        background: hsl(0deg 0% 100% / 3%);

        &:hover {
            background: hsl(0deg 0% 100% / 15%);
        }
    }

    & input[type="text"],
    input[type="email"],
    input[type="password"],
    input[type="number"],
    input[type="url"],
    input[type="date"],
    textarea,
    .new-style .tab-switcher .ind-tab:not(.selected),
    select,
    .pill-container,
    .user-status-content-wrapper {
        background-color: hsl(0deg 0% 0% / 20%);
        border-color: hsl(0deg 0% 0% / 60%);
        color: inherit;
    }

    & select option {
        background-color: hsl(212deg 28% 18%);
        color: hsl(236deg 33% 90%);
    }

    .unread_count,
    /* The actions_popover unread_count object has its own variable CSS,
       and thus needs to be repeated here with all three classes for precedence) */
    .actions_popover .mark_as_unread .unread_count {
        background-color: hsl(105deg 2% 50% / 50%);
    }

    .pill-container {
        border-style: solid;
        border-width: 1px;
    }

    .deactivated-pill {
        background-color: hsl(0deg 86% 14%) !important;
    }

    #search_arrows .pill,
    .pm_recipient .pill-container .pill {
        color: inherit;
        border: 1px solid hsl(0deg 0% 0% / 50%);
        background-color: hsl(0deg 0% 0% / 25%);
        font-weight: 600;
    }

    #search_arrows .pill:focus,
    .pm_recipient .pill-container .pill:focus {
        color: hsl(0deg 0% 100%);
        border: 1px solid hsl(176deg 78% 28% / 60%);
        background-color: hsl(176deg 49% 42% / 40%);
    }

    .new-style .button.no-style {
        background-color: transparent;
    }

    .create_user_group_plus_button,
    .create_stream_plus_button {
        color: hsl(0deg 0% 100%);
        background-color: hsl(0deg 0% 0% / 20%);
        border-color: hsl(0deg 0% 0% / 60%);
    }

    .emoji-info-popover
        .emoji-popover
        .emoji-popover-category-tabs
        .emoji-popover-tab-item.active {
        background-color: hsl(0deg 0% 0% / 50%);
    }

    .new-style .tab-switcher .ind-tab.selected,
    div.message_content thead,
    .table-striped thead th,
    .emoji-popover .reaction.reacted,
    .message_reactions .message_reaction.reacted {
        background-color: hsl(0deg 0% 0% / 50%);
        border-color: hsl(0deg 0% 0% / 90%);
    }

    .ind-tab.disabled {
        color: hsl(0deg 0% 42% / 90%) !important;
    }

    .message_reactions:hover .message_reaction + .reaction_button,
    .message_reactions .message_reaction {
        background-color: transparent;
        border-color: hsl(0deg 0% 0% / 80%);
        color: inherit;

        &:hover {
            border-color: hsl(236deg 33% 90%);
        }
    }

    .emoji-popover .reaction:focus {
        box-shadow: 0 0 1px hsl(0deg 0% 98%);
    }

    & input[type="text"]:focus,
    input[type="email"]:focus,
    input[type="number"]:focus,
    textarea:focus,
    textarea.new_message_textarea:focus,
    .compose_table .recipient_box:focus {
        border-color: hsl(0deg 0% 0% / 90%);
    }

    .message-header-contents,
    .message_header_private_message .message-header-contents {
        background-color: hsl(0deg 0% 0% / 20%);
        border-color: transparent;
    }

    .compose_control_buttons_container .divider {
        color: hsl(236deg 33% 90% / 50%);
    }

    /* Not that .message_row (below) needs to be more contrast on dark theme */
    #compose-content,
    .message_list .recipient_row,
    .message_row,
    .draft-row .draft-info-box,
    .preview_message_area {
        border-color: hsl(0deg 0% 0% / 20%);
    }

    .recipient_row {
        .message_row.unread {
            .date_row {
                background-color: hsl(212deg 28% 18%);
            }
        }

        .private-message.unread {
            .date_row {
                background-color: hsl(208deg 17% 29%);
            }
        }

        .message_row.unread ~ .message_row.unread {
            .date_row {
                background-color: transparent;
            }
        }

        .private-message.unread ~ .private-message.unread {
            .date_row {
                background-color: hsl(208deg 17% 29%);
            }
        }
    }

    .spectator_narrow_login_button,
    .top-navbar-border {
        border-color: hsl(0deg 0% 0% / 60%);
    }

    #message_view_header .sub_count {
        &::before,
        &::after {
            color: hsl(0deg 0% 100% / 50%);
        }
    }

    #message_view_header .stream {
        color: hsl(236deg 33% 90%);
    }

    #message_view_header .sub_count,
    #message_view_header .narrow_description {
        color: hsl(0deg 0% 90%);
    }

    & div.overlay,
    #subscription_overlay
        #stream-creation
        #stream_creation_form
        #stream_creating_indicator:not(:empty),
    #groups_overlay
        #user-group-creation
        #user_group_creation_form
        #user_group_creating_indicator:not(:empty),
    .emoji-info-popover
        .emoji-popover
        .emoji-popover-emoji:not(.reacted):focus {
        background-color: hsl(212deg 28% 8% / 75%);
    }

    & div.overlay .flex.overlay-content > div,
    .dropdown-menu.typeahead,
    #settings_page,
    .informational-overlays .overlay-content {
        box-shadow: 0 0 30px hsl(212deg 32% 7%);
    }

    .tippy-box[data-theme~="light-border"],
    .dropdown-menu ul,
    .dropdown .dropdown-menu,
    .popover,
    .popover-title,
    .popover-content {
        background-color: hsl(212deg 32% 14%);
    }

    .dropdown-menu a {
        color: inherit;
    }

    .dropdown .dropdown-menu li.divider,
    .popover hr,
    hr {
        color: hsl(212deg 28% 18%);
        opacity: 0.2;
    }

    #gear_menu_about_zulip {
        .white_zulip_icon_without_text {
            filter: invert(10%) sepia(16%) saturate(175%) hue-rotate(194deg)
                brightness(99%) contrast(89%);
        }
    }

    #gear-menu {
        .dark-theme {
            display: none;
        }

        .light-theme {
            display: block;
        }

        .dropdown-menu a:hover {
            color: hsl(0deg 0% 100%);
        }
    }

    .nav .dropdown-menu::after,
    .popover.bottom .arrow {
        border-bottom-color: hsl(235deg 18% 7%);
    }

    .popover.left .arrow {
        border-left-color: hsl(235deg 18% 7%);
    }

    .popover.top .arrow {
        border-top-color: hsl(235deg 18% 7%);
    }

    .popover.right .arrow {
        border-right-color: hsl(235deg 18% 7%);
    }

    .narrow_to_compose_recipients,
    .expand_composebox_button,
    .collapse_composebox_button,
    #message_edit_tooltip,
    .clear_search_button,
    .clear_search_button:focus,
    .clear_search_button:active,
    .clear_search_button:disabled:hover,
    #user-groups .save-instructions,
    .close,
    #user_presences li:hover .user-list-sidebar-menu-icon,
    li.top_left_all_messages:hover .all-messages-sidebar-menu-icon,
    li.top_left_starred_messages:hover .starred-messages-sidebar-menu-icon,
    li.top_left_drafts:hover .drafts-sidebar-menu-icon,
    #stream_filters li:hover .stream-sidebar-menu-icon,
    li.topic-list-item:hover .topic-sidebar-menu-icon {
        color: hsl(236deg 33% 80%);
    }

    #message_edit_tooltip:hover,
    .clear_search_button:hover {
        color: hsl(0deg 0% 100%);
    }

    .spectator_login_buttons a {
        color: hsl(236deg 33% 90%);

        &:hover {
            color: hsl(0deg 0% 100%);
        }
    }

    .spectator_narrow_login_button .login_button i {
        color: hsl(236deg 33% 90%);
    }

    #user_presences li .user-list-sidebar-menu-icon:hover,
    .all-messages-sidebar-menu-icon:hover,
    .starred-messages-sidebar-menu-icon:hover,
    .drafts-sidebar-menu-icon:hover,
    .stream-sidebar-menu-icon:hover,
    .topic-sidebar-menu-icon:hover {
        color: hsl(0deg 0% 100%) !important;
    }

    #streamlist-toggle,
    #userlist-toggle {
        color: inherit;
        border-color: hsl(0deg 0% 0% / 60%);
    }

    #streamlist-toggle-button {
        color: inherit;
        background-color: inherit;
    }

    #userlist-toggle-button {
        color: hsl(221deg 9% 54%);

        &:hover {
            color: inherit;
        }
    }

    & li.active-filter,
    li.active-sub-filter {
        background-color: hsl(199deg 33% 46% / 20%);
    }

    :not(.active-sub-filter) {
        &.top_left_row:hover,
        &.bottom_left_row:hover,
        &#stream_filters li.highlighted_stream {
            background-color: hsl(136deg 25% 73% / 20%);
        }
    }

    #stream_filters .narrow-filter.active-filter {
        .topic-list .filter-topics,
        > .bottom_left_row {
            background-color: hsl(208deg 31% 24%);
        }
    }

    .zoom-in {
        #topics_header,
        .narrow-filter > .bottom_left_row,
        #stream_filters .topic-list .filter-topics {
            background-color: hsl(212deg 28% 18%);
        }
    }

    #topics_header {
        .show-all-streams {
            color: hsl(236deg 33% 90%);
            opacity: 0.75;
        }
    }

    #user_presences li:hover,
    #user_presences li.highlighted_user {
        background-color: hsl(136deg 25% 73% / 20%);
    }

    .group-row.active,
    .stream-row.active,
    .emoji-info-popover .emoji-showcase-container,
    .emoji-info-popover .emoji-popover .emoji-popover-category-tabs,
    .emoji-info-popover .emoji-popover .emoji-popover-top {
        background-color: hsl(0deg 0% 0% / 20%);
    }

    .recent_topics_participant_overflow {
        color: hsl(0deg 0% 100%) !important;
        background-color: hsl(211deg 18% 25%) !important;
    }

    .recent_topics_container #recent_topics_table .btn-recent-filters {
        background-color: hsl(211deg 29% 14%);
        border-color: hsl(0deg 0% 0%);
        color: hsl(0deg 0% 100%);

        &:focus {
            background-color: hsl(0deg 0% 0% / 50%) !important;
            outline: 0;
        }

        &.fake_disabled_button {
            cursor: not-allowed;
            opacity: 0.5;

            &:hover {
                background-color: hsl(0deg 0% 0% / 50%);
                border-color: hsl(0deg 0% 0%);
            }
        }
    }

    .recent_topics_container {
        background-color: hsl(212deg 28% 18%) !important;
    }

    #recent_topics_table tr {
        background-color: hsl(212deg 28% 18%);

        &:hover {
            background-color: hsl(208deg 26% 11% / 60%);
        }
    }

    #recent_topics_table .unread_topic {
        background-color: hsl(212deg 30% 22% / 60%);
    }

    .btn-recent-selected,
    #recent_topics_table thead th {
        background-color: hsl(0deg 0% 0%) !important;

        &[data-sort]:hover {
            background-color: hsl(211deg 29% 14%) !important;
        }
    }

    #recent_topics_table td a {
        color: hsl(206deg 89% 74%);
        text-decoration: none;

        &:hover {
            color: hsl(208deg 64% 52%);
        }
    }

    #recent_topics_table {
        border-color: hsl(0deg 0% 0% / 60%);

        .fa-envelope,
        .fa-group {
            opacity: 0.7;
        }
    }

    & thead,
    .drafts-container .drafts-header,
    .nav > li > a:focus,
    .nav > li > a:hover,
    .subscriptions-container .subscriptions-header,
    .user-groups-container .user-groups-header,
    .grey-box,
    .white-box,
    .stream-email,
    #settings_page .settings-header,
    #settings_page .sidebar li.active,
    #settings_page .sidebar-wrapper .tab-container,
    .table-striped tbody tr:nth-child(even) td,
    .table-striped tbody tr:nth-child(odd) th,
    .modal-footer,
    .modal-bg .modal-header {
        border-color: hsl(0deg 0% 0% / 20%);
        background-color: hsl(0deg 0% 0% / 20%);
    }

    .table-striped tbody tr:nth-child(odd) td {
        background-color: hsl(212deg 28% 18%);
    }

    .user-groups-container .right .display-type,
    .subscriptions-container .right .display-type,
    .stream-row,
    .group-row,
    .subscriptions-container .left .search-container,
    .subscriptions-container .left,
    .user-groups-container .left,
    .subscriber-list-box,
    .subscriber-list-box .subscriber_list_container .subscriber-list tr,
    .member-list-box,
    .member-list-box .member_list_container .member-list tr,
    #subscription_overlay .subsection-parent div,
    #subscription_overlay .settings-radio-input-parent,
    #settings_page .sidebar-wrapper,
    #settings_page .sidebar-wrapper *,
    table,
    table th,
    table td {
        border-color: hsl(0deg 0% 0% / 20%);
    }

    .draft-row .draft-info-box,
    .message_header_private_message .message-header-contents {
        box-shadow: none;
    }

    .draft-row .message_header_private_message .message_label_clickable {
        padding: 4px 6px 3px;
        color: inherit;
    }

    .nav-list > li > a,
    .nav-list .nav-header {
        text-shadow: none;
    }

    .group_mention .messagebox,
    .direct_mention .messagebox {
        background-color: hsl(8deg 78% 43% / 15%);
    }

    .rendered_markdown {
        .user-mention,
        .user-group-mention {
            background: linear-gradient(
                to bottom,
                hsl(0deg 0% 0% / 20%) 0%,
                hsl(0deg 0% 0% / 10%) 100%
            );
            box-shadow: 0 0 0 1px hsl(0deg 0% 0% / 40%);
        }

        .user-mention-me :not(.silent) {
            background-color: hsl(355deg 37% 31%);
            box-shadow: 0 0 0 1px hsl(330deg 40% 20%);
        }

        .codehilite code,
        .codehilite pre {
            color: hsl(212deg 100% 82%);
            background-color: hsl(212deg 25% 15%);
        }

        .codehilite .hll {
            background-color: hsl(0deg 0% 13%);
        }

        .codehilite .err {
            color: hsl(1deg 67% 66%);
            background-color: hsl(0deg 7% 22%);
        }

        .codehilite .k {
            color: hsl(31deg 85% 59%);
        }

        .codehilite .p {
            color: hsl(179deg 27% 35%);
        }

        .codehilite .cs {
            color: hsl(0deg 100% 40%);
            font-weight: 700;
        }

        .codehilite .gd {
            color: hsl(0deg 100% 40%);
        }

        .codehilite .ge {
            color: hsl(0deg 0% 80%);
            font-style: italic;
        }

        .codehilite .gr {
            color: hsl(0deg 100% 50%);
        }

        .codehilite .go {
            color: hsl(0deg 0% 50%);
        }

        .codehilite .gs {
            color: hsl(0deg 0% 80%);
            font-weight: 700;
        }

        .codehilite .gu {
            color: hsl(300deg 100% 25%);
            font-weight: 700;
        }

        .codehilite .gt {
            color: hsl(222deg 100% 41%);
        }

        .codehilite .kc {
            color: hsl(0deg 45% 75%);
        }

        .codehilite .kd {
            color: hsl(60deg 100% 76%);
        }

        .codehilite .kn {
            color: hsl(24deg 56% 72%);
            font-weight: 700;
        }

        .codehilite .kp {
            color: hsl(62deg 36% 71%);
        }

        .codehilite .kr {
            color: hsl(359deg 58% 56%);
        }

        .codehilite .ni {
            color: hsl(359deg 35% 63%);
        }

        .codehilite .ne {
            color: hsl(53deg 23% 69%);
            font-weight: 700;
        }

        .codehilite .nn {
            color: hsl(204deg 54% 72%);
        }

        .codehilite .vi {
            color: hsl(60deg 100% 89%);
        }

        .codehilite .c,
        .codehilite .g,
        .codehilite .cm,
        .codehilite .cp,
        .codehilite .c1 {
            color: hsl(209deg 15% 55%);
        }

        .codehilite .l,
        .codehilite .x,
        .codehilite .no,
        .codehilite .nd,
        .codehilite .nl,
        .codehilite .nx,
        .codehilite .py,
        .codehilite .w {
            color: hsl(0deg 0% 80%);
        }

        .codehilite .n,
        .codehilite .nv,
        .codehilite .vg {
            color: hsl(60deg 19% 83%);
        }

        .codehilite .o,
        .codehilite .ow {
            color: hsl(58deg 52% 88%);
        }

        .codehilite .gh,
        .codehilite .gp {
            color: hsl(60deg 19% 83%);
            font-weight: 700;
        }

        .codehilite .gi,
        .codehilite .kt {
            color: hsl(120deg 100% 40%);
        }

        .codehilite .ld,
        .codehilite .s,
        .codehilite .sb,
        .codehilite .sc,
        .codehilite .sd,
        .codehilite .s2,
        .codehilite .se,
        .codehilite .sh,
        .codehilite .si,
        .codehilite .sx,
        .codehilite .sr,
        .codehilite .s1,
        .codehilite .ss {
            color: hsl(0deg 36% 69%);
        }

        .codehilite .m,
        .codehilite .mf,
        .codehilite .mh,
        .codehilite .mi,
        .codehilite .mo,
        .codehilite .il {
            color: hsl(183deg 45% 69%);
        }

        .codehilite .na,
        .codehilite .nt {
            color: hsl(127deg 25% 68%);
        }

        .codehilite .nb,
        .codehilite .nc,
        .codehilite .nf,
        .codehilite .bp,
        .codehilite .vc {
            color: hsl(60deg 75% 75%);
        }
    }

    #message-edit-history {
        .message_edit_history_content {
            .highlight_text_inserted {
                color: hsl(122deg 100% 81%);
                background-color: hsl(120deg 64% 95% / 30%);
            }

            .highlight_text_deleted {
                color: hsl(0deg 90% 67%);
                background-color: hsl(7deg 54% 62% / 38%);
            }
        }
    }

    & time {
        background: hsl(0deg 0% 0% / 20%);
        box-shadow: 0 0 0 1px hsl(0deg 0% 0% / 40%);
    }

    .upgrade-tip,
    .upgrade-or-sponsorship-tip,
    .tip {
        color: inherit;
        background-color: hsl(46deg 28% 38% / 27%);
        border: 1px solid hsl(49deg 38% 46%);
    }

    #request-progress-status-banner {
        background-color: hsl(212deg 32% 14%);

        .alert-content {
            color: hsl(236deg 33% 90%);
        }
    }

    .alert.home-error-bar {
        color: hsl(236deg 33% 90%);
        background-color: hsl(35deg 84% 62% / 25%);
        border: 1px solid hsl(11deg 46% 54%);
    }

    .alert {
        text-shadow: none;

        .close {
            color: inherit;
            opacity: 0.8;
        }

        .close:hover {
            opacity: 1;
        }
    }

    .alert.alert-success {
        color: inherit;
        background-color: hsl(161deg 60% 46% / 20%);
        border-color: hsl(165deg 68% 37%);
    }

    .alert.alert-error,
    .alert.alert-danger {
        background-color: hsl(318deg 12% 21%);
        color: inherit;
        border: 1px solid hsl(0deg 75% 65%);
    }

    .alert-box .alert,
    .alert-box .stacktrace,
    .alert.alert-error {
        background-color: hsl(318deg 12% 21%);
        color: inherit;
        border: 1px solid hsl(0deg 75% 65%);
    }

    .alert-box {
        .alert.alert-error::before {
            color: hsl(0deg 75% 65%);
        }

        .stacktrace {
            color: hsl(314deg 22% 85%);

            .expand {
                color: hsl(318deg 14% 36%);
            }

            .subtle {
                color: hsl(314deg 19% 63%);
            }

            .code-context {
                color: hsl(314deg 27% 82%);
                background-color: hsl(312deg 7% 14%);
                box-shadow: inset 0 11px 10px -10px hsl(0deg 0% 6%),
                    inset 0 -11px 10px -10px hsl(0deg 0% 6%);

                .line-number {
                    color: hsl(318deg 14% 44%);
                }

                .focus-line {
                    background-color: hsl(307deg 9% 19%);
                }
            }
        }
    }

    /* Popover: */
    .hotspot.overlay .hotspot-popover {
        border-color: hsl(0deg 0% 0% / 20%) !important;
        /* Based on the `.hotspot-popover` shadow in `hotspots.css`, but with a new
    color. */
        box-shadow: 0 5px 10px hsl(0deg 0% 0% / 40%);
    }

    #invite-user-modal {
        #clipboard_image {
            & path {
                fill: hsl(236deg 33% 90%);
            }
        }
    }

    #user-profile-modal {
        #default-section {
            .default-field {
                .name {
                    color: hsl(236deg 33% 90%);
                }
            }
        }

        #content {
            .field-section {
                .name {
                    color: hsl(236deg 33% 90%);
                }
            }
        }

        .subscription-group-list,
        .subscription-stream-list,
        .subscription-stream-list .user-stream-list tr,
        .subscription-group-list .user-group-list tr {
            border-color: hsl(0deg 0% 0% / 40%);
        }
    }

    /* Arrows: */
    .hotspot.overlay {
        .hotspot-popover.arrow-right::before {
            border-left-color: hsl(0deg 0% 0% / 20%);
        }

        .hotspot-popover.arrow-right::after {
            border-left-color: hsl(212deg 28% 18%);
        }

        .hotspot-popover.arrow-bottom::before {
            border-top-color: hsl(0deg 0% 0% / 20%);
        }

        .hotspot-popover.arrow-bottom::after {
            border-top-color: hsl(212deg 28% 18%);
        }

        .hotspot-popover.arrow-left::before {
            border-right-color: hsl(0deg 0% 0% / 20%);
        }

        .hotspot-popover.arrow-left::after {
            border-right-color: hsl(212deg 28% 18%);
        }

        .hotspot-popover.arrow-top::before {
            border-bottom-color: hsl(0deg 0% 0% / 20%);
        }

        .hotspot-popover.arrow-top::after {
            border-bottom-color: hsl(212deg 28% 18%);
        }
    }

    /* Content: */
    .hotspot.overlay .hotspot-popover .hotspot-popover-content,
    .hotspot.overlay .hotspot-popover .hotspot-popover-bottom {
        background-color: hsl(212deg 28% 18%);
    }

    .alert-zulip-logo,
    .top-messages-logo,
    .bottom-messages-logo {
        & svg path {
            fill: hsl(214deg 27% 18%);
            stroke: hsl(214deg 27% 18%);
        }

        & svg circle {
            fill: hsl(0deg 0% 100%);
            stroke: hsl(0deg 0% 100%);
        }
    }

    .history-limited-box,
    .all-messages-search-caution {
        background-color: hsl(0deg 0% 0% / 20%);
    }

    #feedback_container,
    code,
    .typeahead.dropdown-menu {
        background-color: hsl(212deg 25% 15%);
        border-color: hsl(0deg 0% 0% / 50%);
        color: inherit;
    }

    /* Search highlight used in both topics and rendered_markdown */
    .highlight {
        background-color: hsl(51deg 100% 64% / 42%);
    }

    .sub-unsub-message span::before,
    .sub-unsub-message span::after,
    .date_row span::before,
    .date_row span::after,
    .streams_subheader span::before,
    .streams_subheader span::after {
        opacity: 0.5;
        border-bottom: 1px solid hsl(0deg 0% 100%);
    }

    .star:not(.empty-star),
    .empty-star:hover {
        color: hsl(126deg 66% 72% / 75%);
    }

    #bots_lists_navbar .active a {
        color: hsl(0deg 0% 87%);
        background-color: hsl(212deg 28% 18%);
        border-color: hsl(0deg 0% 87%);
        border-bottom-color: transparent;
    }

    .searching-for-more-topics img {
        filter: invert(100%);
    }

    .simplebar-track .simplebar-scrollbar::before {
        background-color: hsl(0deg 0% 100%);
        box-shadow: 0 0 0 1px hsl(0deg 0% 0% / 33%);
    }

    .collapse-settings-btn:hover {
        color: hsl(200deg 79% 66%);
    }

    #request-progress-status-banner .loading-indicator,
    #loading_older_messages_indicator,
    #recent_topics_loading_messages_indicator {
        & path {
            fill: hsl(0deg 0% 100%);
        }
    }

    .small_square_button {
        &.small_square_x {
            background-color: hsl(0deg 0% 95%);
            color: hsl(0deg 0% 42%);

            &:hover {
                color: hsl(0deg 0% 18%);
            }
        }
    }

    & a:not(:active):focus,
    button:focus,
    .new-style label.checkbox input[type="checkbox"]:focus ~ span,
    i.fa:focus,
    i.zulip-icon:focus,
    .auto-select:focus,
    [role="button"]:focus {
        outline-color: hsl(0deg 0% 67%);
    }

    .animated-purple-button:focus {
        box-shadow: 0 1px 4px 0 hsl(0deg 0% 100% / 66.6%);
    }

    .color_animated_button {
        background-color: hsl(211deg 29% 14%);

        * {
            color: hsl(0deg 0% 100%);
        }

        &:hover {
            background-color: hsl(240deg 96% 68%);
        }
    }

    /* Widgets: Poll */
    .poll-widget {
        .poll-vote {
            color: hsl(185deg 35% 65%);
            border-color: hsl(185deg 35% 35%);

            &:hover {
                color: hsl(185deg 50% 70%);
                border-color: hsl(185deg 40% 40%);
                background-color: hsl(185deg 20% 20%);
            }

            &:focus {
                color: hsl(185deg 50% 65%);
                border-color: hsl(185deg 40% 50%);
                background-color: hsl(185deg 40% 35%);
            }
        }

        .poll-names {
            color: hsl(236deg 15% 70%);
        }
    }

    /* Widgets: Todo */
    .todo-widget {
        & label.checkbox {
            & input[type="checkbox"] {
                ~ span {
                    border-color: hsl(185deg 40% 45%);
                    opacity: 0.7;
                }

                &:hover ~ span {
                    background-color: hsl(185deg 20% 20%);
                    border-color: hsl(185deg 40% 35%);
                }

                &:checked ~ span {
                    background-color: hsl(185deg 40% 45%);
                }

                &:focus ~ span {
                    outline-color: hsl(0deg 0% 100% / 0%);
                }
            }
        }
    }

    /* Originally the icon inherits the color of label, but when the setting
    is disabled, the color of the label is changed and thus the icon becomes
    too light. So, we set the color explicitly to original color of label to
    keep the color of the icon same even when the setting is disabled. */
    #id_realm_enable_spectator_access_label a {
        color: hsl(236deg 33% 90%);
    }

    #stream-specific-notify-table .unmute_stream {
        &:hover {
            color: hsl(0deg 0% 100%);
        }
    }

    #read_receipts_modal #read_receipts_list li {
        &:hover {
            background-color: hsl(0deg 0% 100% / 5%);
        }

        &:active,
        &:focus {
            background-color: hsl(0deg 0% 100% / 10%);
        }
    }

    #settings_page,
    #stream_settings {
        .save-button-controls .discard-button {
            color: hsl(0deg 0% 80%);

            &:hover {
                .save-discard-widget-button-text {
                    color: hsl(0deg 0% 100%);
                }
            }
        }
    }
}

@supports (-moz-appearance: none) {
    %dark-theme #settings_page select {
        background-color: hsl(0deg 0% 0% / 20%);
    }
}

:root.dark-theme {
    @extend %dark-theme;
}

@media (prefers-color-scheme: dark) {
    :root.color-scheme-automatic {
        @extend %dark-theme;
    }
}

~~~
#### billing.css ####
~~~
.billing-upgrade-page {
    font-family: "Source Sans 3", sans-serif;
    background-color: hsl(0deg 0% 98%);
    height: 100vh;

    .hero {
        background-color: hsl(153deg 32% 55%);
        color: hsl(153deg 32% 55%);
        position: absolute;
        top: 0;
        width: 100%;
    }

    .small-hero {
        padding: 120px 50px 0;
    }

    .main {
        width: 800px;
        max-width: 90%;
        margin: 0 auto;
    }

    & h1 {
        margin: 30px 0;
        font-weight: bold;
    }

    .nav {
        margin-bottom: 0;
    }

    .nav-tabs {
        border-bottom: 0;
        font-size: 1.2em;

        & a {
            font-weight: bold;
        }
    }

    .tab-content {
        border: 1px solid hsl(0deg 0% 87%);
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        padding: 20px;
        background-color: hsl(0deg 0% 100%);
        font-size: 1.1em;
    }

    .support-link {
        margin: 10px 20px;

        & a,
        a:hover,
        a:visited {
            color: hsl(170deg 47% 33%);
            font-weight: 500;
        }
    }

    .license-management,
    .payment-schedule {
        & label {
            display: inline-block;
        }

        & input[type="radio"] {
            display: none;

            &:checked {
                + .box {
                    background-color: hsl(153deg 32% 55%);
                    color: hsl(0deg 0% 100%);
                    border-color: hsl(152deg 33% 39%);
                }
            }
        }

        .box {
            width: 120px;
            height: 70px;
            background-color: hsl(0deg 0% 94%);
            transition: all 0.2s ease;
            display: inline-block;
            text-align: center;
            cursor: pointer;
            position: relative;
            border: 1px solid hsl(0deg 0% 91%);
            border-radius: 8px;
            margin: 0 10px 5px 0;
            padding: 30px 20px;
            vertical-align: top;

            &:hover {
                background-color: hsl(0deg 0% 91%);
                border-color: hsl(0deg 0% 80%);
            }

            .schedule-time {
                font-weight: bold;
                font-size: 1.2em;
                margin-top: 10px;
            }

            .schedule-amount {
                margin-top: 5px;
                font-size: 1.1em;
                height: 50px;
            }

            .schedule-amount-2 {
                font-size: 0.9em;
            }

            .management-type {
                font-weight: bold;
                font-size: 1.2em;
                margin-top: 10px;
            }

            .management-type-text {
                font-size: 1.1em;
                margin-top: 5px;
            }
        }
    }

    .stripe-button-el {
        padding: 11px 25px;
        font-weight: 400;
        color: hsl(0deg 0% 100%);
        background: linear-gradient(
            145deg,
            hsl(191deg 56% 55%),
            hsl(169deg 65% 42%)
        );
        box-shadow: 0 3px 10px hsl(0deg 0% 0% / 20%);
        border: 0;
        height: 40px;
        margin: 5px 0 0;

        & span {
            background: 0;
            box-shadow: none;
            font-family: "Source Sans 3", sans-serif;
            line-height: 20px;
        }
    }

    .stripe-button-el:hover {
        background-color: hsl(169deg 65% 42%);
        box-shadow: 0 3px 10px hsl(0deg 0% 0% / 30%);
    }

    .stripe-button-el:active,
    .stripe-button-el:enabled:active {
        background-color: hsl(169deg 70% 32%);

        & span {
            background: 0;
            box-shadow: none;
        }
    }

    .stripe-button-el:disabled {
        & span {
            background: none;
        }
    }

    .stripe-button-el:hover:disabled {
        box-shadow: none;
        background-color: hsl(0deg 0% 78%);
        pointer-events: none;
    }

    .invoice-button {
        font-size: 19px;

        &:disabled {
            opacity: 0.5;
            cursor: not-allowed;

            &:hover {
                pointer-events: all;
            }
        }
    }

    .upgrade-button-container {
        display: inline-block;
    }

    #manual_license_count,
    #invoiced_licenses {
        width: 50px;
    }

    #licenses_at_next_renewal_input,
    #new_licenses_input {
        width: 206px;
    }

    #error-message-box {
        margin-top: 10px;
        font-weight: 600;
        display: none;
    }

    #restartsession-loading,
    #webhook-loading,
    #sponsorship-loading,
    #planchange-loading,
    #licensechange-loading,
    #cardchange-loading,
    #invoice-loading,
    #autopay-loading {
        display: none;
        min-height: 55px;
        text-align: center;
    }

    #restartsession-success,
    #webhook-success,
    #sponsorship-success,
    #planchange-success,
    #licensechange-success,
    #cardchange-success,
    #invoice-success,
    #autopay-success {
        text-align: center;
        display: none;
    }

    #restartsession-error,
    #webhook-error,
    #sponsorship-error,
    #planchange-error,
    #licensechange-error,
    #cardchange-error,
    #invoice-error,
    #autopay-error {
        text-align: center;
        display: none;
    }

    .zulip-loading-logo {
        margin: 0 auto;
        width: 24px;
        height: 24px;
    }

    .zulip-loading-logo svg circle {
        fill: hsl(0deg 0% 27%);
        stroke: hsl(0deg 0% 27%);
    }

    .zulip-loading-logo svg path {
        fill: hsl(0deg 0% 100%);
        stroke: hsl(0deg 0% 100%);
    }

    #restartsession_loading_indicator,
    #webhook_loading_indicator,
    #sponsorship_loading_indicator,
    #planchange_loading_indicator,
    #licensechange_loading_indicator,
    #cardchange_loading_indicator,
    #invoice_loading_indicator,
    #autopay_loading_indicator {
        margin: 10px auto;
    }

    #restartsession_loading_indicator_box_container,
    #webhook_loading_indicator_box_container,
    #sponsorship_loading_indicator_box_container,
    #planchange_loading_indicator_box_container,
    #licensechange_loading_indicator_box_container,
    #cardchange_loading_indicator_box_container,
    #invoice_loading_indicator_box_container,
    #autopay_loading_indicator_box_container {
        position: absolute;
        left: 50%;
    }

    #restartsession_loading_indicator_box,
    #webhook_loading_indicator_box,
    #sponsorship_loading_indicator_box,
    #planchange_loading_indicator_box,
    #licensechange_loading_indicator_box,
    #cardchange_loading_indicator_box,
    #invoice_loading_indicator_box,
    #autopay_loading_indicator_box {
        position: relative;
        left: -50%;
        top: -41px;
        z-index: 10;
        border-radius: 6px;
    }

    #restartsession_loading_indicator .loading_indicator_text,
    #webhook_loading_indicator .loading_indicator_text,
    #sponsorship_loading_indicator .loading_indicator_text,
    #planchange_loading_indicator .loading_indicator_text,
    #licensechange_loading_indicator .loading_indicator_text,
    #cardchange_loading_indicator .loading_indicator_text,
    #invoice_loading_indicator .loading_indicator_text,
    #autopay_loading_indicator .loading_indicator_text {
        margin-left: -25px;
    }

    #license-automatic-section,
    #license-manual-section {
        display: none;
    }

    & select,
    input,
    textarea {
        font-family: inherit;
    }
}

input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
    appearance: none;
    margin: 0;
}

input[name="licenses"] {
    appearance: textfield;
}

#sponsorship-form {
    & input {
        box-sizing: border-box;
        height: 30px;
    }

    & textarea {
        box-sizing: border-box;
        color: hsl(0deg 0% 33%);
        background-color: hsl(0deg 0% 100%);
        border-radius: 4px;
        vertical-align: middle;
        border: 1px solid hsl(0deg 0% 80%);
        padding: 4px 6px;
        margin-bottom: 10px;
        line-height: 20px;

        box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%);
        transition: border linear 0.2s, box-shadow linear 0.2s;

        &:focus {
            border-color: hsl(206.5deg 80% 62% / 80%);
            outline: 0;

            box-shadow: inset 0 1px 1px hsl(0deg 0% 0% / 7.5%),
                0 0 8px hsl(206.5deg 80% 62% / 60%);

            &:invalid {
                border-color: hsl(2deg 81% 55%);
                box-shadow: 0 0 6px hsl(2deg 82% 85%);
                color: hsl(1deg 45% 50%);
            }
        }
    }

    & select {
        height: 30px;
        width: 100%;
        padding: 4px 6px;
        font-size: 14px;
        color: hsl(0deg 0% 33%);
        border-radius: 4px;
        border: 1px solid hsl(0deg 0% 80%);
        margin-bottom: 10px;
        cursor: pointer;
        background-color: hsl(0deg 0% 100%);
    }

    & input[name="website"] {
        width: 100%;
    }

    & textarea[name="description"] {
        width: 100%;
    }
}

~~~
#### informational_overlays.css ####
~~~
.informational-overlays {
    .overlay-content {
        /* because zoom breaks at 525px perhaps due to rounding errors, so add a
           trivial amount of width so it doesn't break. */
        width: 550px;
        margin: 0 auto;
        position: relative;
        top: calc((30vh - 50px) / 2);
        border-radius: 4px;
        overflow: hidden;

        background-color: hsl(0deg 0% 100%);
    }

    .overlay-tabs {
        padding: 10px 0;
        border-bottom: 1px solid hsl(0deg 0% 0% / 20%);

        .tab-switcher {
            margin-left: 15px;
        }

        .exit {
            float: right;
            font-size: 1.5rem;
            color: hsl(0deg 0% 67%);
            font-weight: 600;
            margin: 0 15px;
            cursor: pointer;
        }
    }

    .overlay-modal {
        padding-bottom: 10px;

        .modal-header h3 {
            font-weight: 300;
        }

        .modal-body {
            height: 70vh;
            text-align: center;
            outline: none;

            .help-table {
                table-layout: fixed;
            }

            & th {
                font-weight: 400;
            }
        }
    }

    & td.operator {
        font-size: 0.9em;
    }
}

.hotkeys_table {
    table-layout: fixed;
    width: 100%;
    vertical-align: middle;
    display: table;

    & td.definition {
        /* keeps dividing line at same width for all tables in model. */
        width: calc(50% - 11px);
        text-align: right;
    }

    .hotkey {
        font-weight: normal;
    }

    .small_hotkey {
        font-size: 0.9em !important;
        line-height: 12px;

        & kbd {
            font-size: 0.9em;
        }
    }

    .arrow-key {
        font-size: 1.36em;
        line-height: 1;
        padding: 0 0.2em 0.2em;
    }

    & th {
        width: 245px;
        text-align: center;
        /* aligns table name with dividing line */
    }

    & td:not(.definition) {
        text-align: left;
        white-space: normal;
        font-weight: bold;
    }
}

#keyboard-shortcuts table {
    margin-bottom: 10px !important;
}

@media only screen and (width < $md_min) {
    .informational-overlays {
        .overlay-content {
            width: calc(100% - 20px);
        }

        .tab-switcher {
            display: flex;

            &.large .ind-tab {
                width: 100%;
            }
        }

        .table.table-condensed.table-striped {
            margin-left: auto;
            margin-right: auto;
        }

        .hotkeys_table {
            width: 100%;
            display: table;
        }
    }
}

~~~
#### user_status.css ####
~~~
#set-user-status-modal {
    /* A narrower width is more attractive for this modal. */
    width: 384px;

    .user-status-content-wrapper {
        display: flex;
        border: 1px solid;
        border-color: hsl(0deg 0% 0% / 60%);
        border-radius: 5px;

        & input.user-status {
            width: 95%;
            border: none;
            background-color: transparent;
            padding-right: 25px;

            @media (width < $ml_min) {
                width: 92%;
            }
        }

        .status-emoji-wrapper {
            height: 20px;
            width: 22px;
            padding: 8px 8px 1px;
            border-right: 1px solid;
            border-color: inherit;
            cursor: pointer;

            .selected-emoji {
                width: 20px;
                height: 20px;
                cursor: pointer;
                /*
                    the following rule is not necessarily better than the one
                    from a6bef5154197b15c20445526fd3f219b4f2e5379 but it works.
                */
                top: -2px;
            }

            /* For custom emojis and smiley icon to take full width. */
            & img.selected-emoji,
            .smiley-icon {
                min-width: 20px;
            }

            .smiley-icon {
                display: block;
                font-size: 18px;
                position: relative;
                top: -2px;
                left: 2px;

                &:hover {
                    text-decoration: none;
                }
            }
        }
    }

    .user-status-options {
        padding-top: 15px;
        padding-left: 2px;

        & button.user-status-value:hover {
            /* Important is required for generic night them styling to not
               have precedence over this. */
            color: hsl(200deg 100% 40%) !important;
        }

        .user-status-value {
            width: 100%;
            text-align: left;
            margin-bottom: 10px;
            line-height: 1.1em;

            .status-emoji {
                height: 18px;
                width: 18px;
                margin-left: 3px;
                margin-right: 3px;
                top: 2px;
            }
        }
    }
}

~~~
### ARE YOU NOT CONVINCED THAT CSSS IS F***ING AWESOME? ###
