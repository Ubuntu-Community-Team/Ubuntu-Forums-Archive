---
title: "lucid swfdec firefox problem solved (recurring) after upgrade from karmic"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Claus7 on 2010-04-15
Hello,

I would like to post my experience, after upgrading from karmic to lucid with flashplayer on mozilla-firefox.

In karmic things were working nicely, both in opera and firefox. In general firefox was working slightly better I should say.

After the upgrade, firefox stop playing flashplayer videos. If I was trying to find which player was installed by default, I came out with swfdec 0.8.2 version. In some cases I had the option to save the flash content with just one click away, yet these instances were far in between.

So, in order to make firefox operating normally with flash videos I went to synaptic and removed the swfdec-mozilla package, while installing flashplugin-nofree.

After that all videos were playing normally.

I say that as recurring, as I have found it more or less in other instances, yet this happened to me while upgrading and not on a fresh install.

I provide a pic on the options firefox had for flash after the procedure described. Initially there was another shockwave flash section, which was removed, after the removal of swfdec package.

Regards!

PS: Firefox was not open at the moment of installing and unistalling.

---

### Post by Claus7 on 2010-04-16
Hello,

...the problem with the above configuration was the annoying:
> Go Updgrade 
message from you tube web site, when working with opera!...

I installed anew the swfdec package, reinstalled opera from deb file... no matter what, this thing was not working.

So, in order to avoid the above message and have flash working both in opera and firefox try the following:

Go in opera to Tools -> Preferences and select the tab advanced (last one on the right).

Then (see pic, which is in hellenic language, but does the trick), pick up on the left side the option: downloads (4th one) and on the right hand side now the option: plugins (3rd one).

From there a new window will pop up, in which you will choose the: change path option. From there a final window will appear, and from there you will keep selected the choices I have made:
/usr/lib/opera/plugins
/usr/lib/flashplugin-installer

With only the first one I could not get rid of the aforementioned message.

Hope this cleared the issue,
Regards!

---

### Post by lovinglinux on 2010-04-16
This is a recurring subject. For future reference see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Claus7 on 2010-04-16
Hello *lovinglinux* once again!

First of all thanks for your response. The web page you have created is really ...enormous!
I think that you should start developing things straight away, rather than providing optimization guides, which are helpful indeed.

Thing is that at least the solution I tried worked somehow, without so much tweaking. Things are working pretty nicely now and I just use firefox for backup browser. So, I want them both working, yet opera is my numero 1.

In addition, the go upgrade message I was getting from you tube about flash, was really annoying, and I did not find a proper solution on ubuntu forums. 

Also I would like to add, that with swfdec, I was able to download straight away the content of a flash video to my computer with just one click away. The bad thing was that one out of ten I was allowed to watch that video in my browser. Think swfdec might have a great potential. I think that I have used it in the past, with good results. I think that the guys of [swfdec]("http://swfdec.freedesktop.org/wiki/")should have a credit for their project as is still in heavy development. Opera in the beginning was working pretty nicely I should say, so something else might have caused the problem in firefox (as I have seen you mention conflicting plugins so this might have been the case...).

Glad to see you again,
hope this thread helps a little, while also pointing to your web page about the comprehensive guide about firefox.

EDIT: I would like to add that with flash I do get a high cpu usage, yet I do not tweak anything at least for now. Your suggestions will be in mind though. 

Regards!

---

### Post by lovinglinux on 2010-04-16
Hi,

> **Claus7 said:**
> I think that you should start developing things straight away, rather than providing optimization guides, which are helpful indeed.

I don't have the skills :)

> **Claus7 said:**
> Thing is that at least the solution I tried worked somehow, without so much tweaking.

> **Claus7 said:**
> ...so something else might have caused the problem in firefox (as I have seen you mention conflicting plugins so this might have been the case...)

Is the same problem and same solution. What happens is that you can only have one plugin of the same type enabled in Firefox. If you have two, one will always take over the content. So even having the plugin from Adobe, swfdec was actually the one rendering flash content. Removing it solves the problem.

---

