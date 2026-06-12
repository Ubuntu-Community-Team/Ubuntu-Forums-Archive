---
title: "Trouble with mozilla"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by gachupin on 2010-10-26
Hi all!
I am having issues with my firefox. The installed version is 3.6 and it simply won't load properly. What happens is that firefox looks like its loading but simply freezes at the "restoring previous session" stage. Any know what the issue might be? I am very new to ubuntu but firefox worked fine earlier and this just suddenly happened, I can't remember if I installed something first or not. Are there any troubleshooting options? Maybe a way to just start firefox and skip the troubleshooting part? How do i COMPLETLY unistall firefox and reinstall? (i tried but don't know if i uninstalled properly)

Thanks to anyone who answers or tries to :)

PS. no error message in terminal

---

### Post by spcwingo on 2010-10-26
Try this command in a terminal:

```
mv ~/.mozilla/firefox ~/.mozilla/firefox.bak
```

If that will at least get Firefox to start I'll help you put your bookmarks back in the new profile it creates.  ;)

---

