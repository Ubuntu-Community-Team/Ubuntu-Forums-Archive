---
title: "Edubuntu hasn't got menu icons"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by mysfit_i on 2007-05-23
I have just completed a clean install of Edubuntu 7.04 and none of the drop down menus from Applications / Places / System have any icons next to them.  How do I get these icons back?

I do not know if it is related but when I go to System > Preferences > Theme I get an error:
The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly.

Unfortunately this means nothing to me and I wouldn't know where to start to correct the problem.  I have installed some themes but I still get the same error and metacity is installed.

My gconf path file looks like this:

######################
# 1. Forced settings #
######################

# Settings forced by the local administrator
xml:readonly:/etc/gconf/gconf.xml.mandatory

# Other forced sources imagined by the local administrator
include /etc/gconf/2/local-mandatory.path


#######################
# 2. User Preferences #
#######################

# mandatory path for sabayon
include "$(HOME)/.gconf.path.mandatory"

# mandatory path for desktop-profiles
include $(ENV_MANDATORY_PATH)

# Other sources imagined by the user
include "$(HOME)/.gconf.path"

# The default storage location, ~/.gconf
# This should be the only readwrite source
xml:readwrite:$(HOME)/.gconf

# default path for sabayon
include "$(HOME)/.gconf.path.defaults"

# default path for desktop-profiles
include $(ENV_DEFAULTS_PATH)


######################
# 3. System defaults #
######################

# Other default sources imagined by the local administrator
include /etc/gconf/2/local-defaults.path

# System administrator's defaults. This source also serves as a legacy
# source for packages not using a recent dh_gconf, or for applications
# installed by hand.
xml:readonly:/etc/gconf/gconf.xml.defaults

# Debian branding, including CDD or packaged branding
xml:readonly:/var/lib/gconf/debian.defaults

# Upstream application defaults
xml:readonly:/var/lib/gconf/defaults

Is anybody able to help me?

---

