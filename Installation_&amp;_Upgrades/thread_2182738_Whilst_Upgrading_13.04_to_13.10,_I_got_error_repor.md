---
title: "Whilst Upgrading 13.04 to 13.10, I got error report &quot;failed to open Package Manager&quot;"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by a.leeming on 2013-10-22
Upgrading to 13.10 I recieved an error report "failed to open Package Manager":   	 	 	 	   _Error report:_
 

 E: Encountered a section with no Package: header  
 E: Problem with MergeList /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-en 
 E: The package lists or status file could not be parsed or opened.  
 E: _cache->open() failed, please report.  

Trouble is I cannot get to "Settings" to change the mirrors. Any ideas?
a.leeming

---

### Post by ibjsb4 on 2013-10-22
You can also get to settings by [opening a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
software-properties-gtk
```

But your problem is not the mirror, its ..

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&sa=Search&cof=FORID:9)

Need further assistance?  Just post back :)

---

### Post by a.leeming on 2013-11-03
Thanks [**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120"). Sorry about the delay in replying. The code 'software-properties-gtk' helped me reset the repositories,
a.leeming
helped

---

### Post by ibjsb4 on 2013-11-03
Are you error free now?  To check for errors in terminal:

```
sudo apt-get update
```

---

