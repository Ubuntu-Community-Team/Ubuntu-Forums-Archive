---
title: "Problems with updateing (and upgradeing)"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by Random20210831 on 2012-08-21
I can not update Weather Indicator with Update Manager. This is the terminal log:

```

```installArchives() failed: perl: warning: Setting locale failed. perl:
warning: Please check that your locale settings:    LANGUAGE = (unset),
    LC_ALL = (unset),   LANG = "sr_RS.utf_8_latin"
    are supported and installed on your system. perl: warning: Falling back to the standard locale ("C"). locale: Cannot set LC_CTYPE to
default locale: No such file or directory locale: Cannot set
LC_MESSAGES to default locale: No such file or directory locale:
Cannot set LC_ALL to default locale: No such file or directory perl:
warning: Setting locale failed. perl: warning: Please check that your
locale settings:    LANGUAGE = (unset),     LC_ALL = (unset),   LANG =
"sr_RS.utf_8_latin"
    are supported and installed on your system. perl: warning: Falling back to the standard locale ("C"). locale: Cannot set LC_CTYPE to
default locale: No such file or directory locale: Cannot set
LC_MESSAGES to default locale: No such file or directory locale:
Cannot set LC_ALL to default locale: No such file or directory perl:
warning: Setting locale failed. perl: warning: Please check that your
locale settings:    LANGUAGE = (unset),     LC_ALL = (unset),   LANG =
"sr_RS.utf_8_latin"
    are supported and installed on your system. perl: warning: Falling back to the standard locale ("C"). locale: Cannot set LC_CTYPE to
default locale: No such file or directory locale: Cannot set
LC_MESSAGES to default locale: No such file or directory locale:
Cannot set LC_ALL to default locale: No such file or directory perl:
warning: Setting locale failed. perl: warning: Please check that your
locale settings:    LANGUAGE = (unset),     LC_ALL = (unset),   LANG =
"sr_RS.utf_8_latin"
    are supported and installed on your system. perl: warning: Falling back to the andard locale ("C"). locale: Cannot set LC_CTYPE to
default locale: No such file or directory locale: Cannot set
LC_MESSAGES to default locale: No such file or directory locale:
Cannot set LC_ALL to default locale: No such file or directory Setting
up indicator-weather (11.11.28-0ubuntu1.1) ... Installing
indicator-specific icons... [B]Installing indicator dconf schema... cp:
cannot stat
`/usr/share/indicator-weather/indicator-weather.gschema.xml': No such
file or directory dpkg: error processing indicator-weather[/B]
(--configure):  subprocess installed post-installation script returned
error exit status 1 Errors were encountered while processing: 
indicator-weather Error in function:  SystemError: E:Sub-process
/usr/bin/dpkg returned an error code (1) Setting up indicator-weather
(11.11.28-0ubuntu1.1) ... Installing indicator-specific icons...
Installing indicator dconf schema... cp: cannot stat
`**/usr/share/indicator-weather/indicator-weather.gschema.xml**': No such
file or directory dpkg: error processing indicator-weather
(--configure):  subprocess installed post-installation script returned
error exit status 1```

```



I've bolded what is probably the most important thing.

---

### Post by darkod on 2012-08-23
I have no idea about this package but usually you can fix broken packages with something like:
sudo apt-get install -f

See if that helps.

If not, you can try removing the package completely (with purge) and reinstalling it.

---

### Post by Random20210831 on 2012-08-23
I am reinstalled Weather Indicator and now that works.

---

