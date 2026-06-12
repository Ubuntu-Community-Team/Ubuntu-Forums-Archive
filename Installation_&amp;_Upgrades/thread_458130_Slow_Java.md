---
title: "Slow Java"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by penguinpower80 on 2007-05-29
I just upgrade to Feisty without any problems (or so I thought).  But ever since then, my Java has been really slow to launch.  

Applets in web pages time out, and even running jcontrol (or ControlPanel) takes about 5 or 6 minutes to launch and the same to shut down.  

This all worked fine before the upgrade.  I am using the sun-java6 package installed through apt.  I have tried removing it and installing the gjr java, but then java didn't work at all.  I reinstalled the sun version and it works again, but still slow.  

I have also run 

update-java-alternatives -s java-6-sun  

and that seems to run without errors.  I have some java apps that I have to get running, so any help would be really appreciated.

Also, if this is in the wrong place, let me know!

Thanks

---

### Post by mlind on 2007-05-29
I've experienced big problems with applets when using Sun's Java 1.6. Try installing sun-java-5-plugin from the Ubuntu repositories and update-java-alternatives to use that plugin instead.

This command shows the plugins currently in use for firefox
```

firefox about:plugins

```

Make sure firefox uses java 1.5 plugin.

---

### Post by penguinpower80 on 2007-05-30
Thanks mlind - I went back to Sun Java 5 and it took care of all my problems both in firefox and just running java apps...so much for progress.

Penguinpower80.

---

### Post by doorknob60 on 2007-12-06
Sorry to bump an old topic, but I need to say downgrading java from 6 to 5 sped it up a lot, although still slower than Windows was with way less RAM...oh well thanks.

---

### Post by TheExplorer on 2008-03-13
I can confirm java applets and its config panel to be extremely slow.
1) Installed Java Update 5
2) Tried FF to verify java installation - took a lot of time...
3) Tried Opera to verify - instant result: Congratulations! You have the latest update...

What's the problem then?

---

