---
title: "I want a safe method to upgrade from Edgy to Gutsy please..."
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by Del Piero on 2007-12-31
I am using the nvidia drivers installed using Envy, and i have Beryl, how do i upgrade to gutsy with Compiz Fusion without problems?

---

### Post by Hmarroqu on 2007-12-31
I would say....back up everything first...then use the update manager to go upgrade one by one. that seems safe to me...

---

### Post by Del Piero on 2007-12-31
> **Hmarroqu said:**
> I would say....back up everything first...then use the update manager to go upgrade one by one. that seems safe to me...

I backed up everything but what do you mean one by one? and i don't see the pop up upgrade, sorry i am a noob. Someone also told me it's better to remove beryl along with the envy drivers before trying it because it already comes with Compiz Fusion and it may cause problems.

---

### Post by meindian523 on 2007-12-31
The best way is to clean-install and overwrite your Edgy.

But if you have waited so long,why not just upgrade when Heron comes out?The Ubuntu release is a LTS too.If you want to install C-F,you can use Forlong's guide....

---

### Post by Del Piero on 2007-12-31
> **meindian523 said:**
> The best way is to clean-install and overwrite your Edgy.

But if you have waited so long,why not just upgrade when Heron comes out?The Ubuntu release is a LTS too.If you want to install C-F,you can use Forlong's guide....

Live CD's never worked for me, i have to install using alternate install. I am also not aware how to install without changing your old settings and deleting your old programs etc. And what is C-F? sorry i am still a noob so i need more details and thanks for taking time to reply.

---

### Post by forestpixie on 2007-12-31
> WARNING: you will have to remove the driver you installed with Envy before upgrading Debian or Ubuntu to a newer release (e.g. upgrading Ubuntu Edgy to Ubuntu Feisty or Debian Etch to Debian Lenny).

You will have to type the following command:

sudo envy --uninstall-all 

from the envy page

I also read about removing beryl, and I think you'll need to make sure you don't have 3rd party repos in your sources.list

Edit - you can't upgrade across versions - might be able to go from one LTS to another but not sure, so you'll have to upgrade one by one - have no idea how mnay that is - at least three

---

### Post by Del Piero on 2007-12-31
> **forestpixie said:**
> from the envy page

I also read about removing beryl, and I think you'll need to make sure you don't have 3rd party repos in your sources.list

Edit - you can't upgrade across versions - might be able to go from one LTS to another but not sure, so you'll have to upgrade one by one - have no idea how mnay that is - at least three

How do i remove 3rd party repos from the sources.list?
How do i uninstall beryl?
How do i upgrade when i have no notifications?

From what you said, am gonna have to jump to Feisty then Gutsy?

What else am gonna lose beside xorg?

And does gutsy really comes with compiz fusion pre-installed?

---

### Post by meindian523 on 2007-12-31
C-F is Compiz-Fusion.

> Live CD's never worked for me, i have to install using alternate install
How does that matter?You are just going to overwrite Edgy's / with Gutsy's / and it won't be possible to save your programs.All of them would be overrun by newer versions.You can save your settings by backing up all the "." folders in your /home/username folder.Press Ctrl+H to see them.

1]You open System>>Administration>>Software Sources and untick all repositories in the Third-Party Software tab.
2]You can do this:
```

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

```

if you are sure you don't want to clean-install.

Yup,you will have to first get to Feisty,then Gutsy unless you clean-install.

---

### Post by Del Piero on 2007-12-31
For example i have conky, ubuntu does not come with conky and it took me an awful lot of time to configure it the way i want. Also it took me alot of time to configure the sound with Alsa and Esd and ages to change my ip from static to dynamic to be able to port forward, will i lose that?

---

### Post by forestpixie on 2007-12-31
yea comes with compiz-fusion but not the settings manager - you'll have to get that after

---

### Post by meindian523 on 2007-12-31
you can remove Beryl using Synaptic.

Search for Beryl in Synaptic and mark all the results which have green boxes next to them for removal.Beware that for this you will have to keep the repositories from where you installed Beryl enabled in Software Sources.

---

### Post by Del Piero on 2007-12-31
You guys rock seriously thanks for taking interest, but will i lose the settings i mentioned in my previous post with a fresh install? can they be lost in case of an upgrade? i am willing to upgrade through 10 versions if it means not losing these things really, along with other customizations i made in this system of course.

---

### Post by Del Piero on 2007-12-31
> **meindian523 said:**
> you can remove Beryl using Synaptic.

Search for Beryl in Synaptic and mark all the results which have green boxes next to them for removal.Beware that for this you will have to keep the repositories from where you installed Beryl enabled in Software Sources.

Thanks man...

---

### Post by bapoumba on 2007-12-31
In any case, I would not recommend to dist-upgrade from Edgy to Gutsy.
To the OP: do you have a separate /home partition ?

---

### Post by Del Piero on 2007-12-31
> **bapoumba said:**
> In any case, I would not recommend to dist-upgrade from Edgy to Gutsy.
**To the OP: do you have a separate /home partition ?**

No..

---

### Post by Del Piero on 2007-12-31
> **Del Piero said:**
> For example i have conky, ubuntu does not come with conky and it took me an awful lot of time to configure it the way i want. Also it took me alot of time to configure the sound with Alsa and Esd and ages to change my ip from static to dynamic to be able to port forward, will i lose that?

Can these things be lost? it's really important so sorry if i am asking alot...

---

### Post by meindian523 on 2007-12-31
> **bapoumba said:**
> In any case, I would not recommend to dist-upgrade from Edgy to Gutsy.
To the OP: do you have a separate /home partition ?

+1.That's why I recommended a clean-install first of all.

---

### Post by bapoumba on 2007-12-31
This is the point about a separate /home. Some settings are kept along when you reinstall. A jump two releases ahead will probably not work (+1 meindian523 ;))

One thing to do is backup all your /home, including hidden files (the ones starting with a "."), on a removable support. Important stuff should be backed up on two different supports.

For network, I usually backup /etc/network/interfaces, /etc/resolv.conf and /etc/apt/apt.conf (this last one because my work uses a proxy).
For the sound issue, it depends what were the issues in the first place. May be a new kernel will fix your problems, may be not. Search UF for your specific sound card and gutsy.
Conky, I do not know. I guess there are config files you can backup and restaure.

You can reinstall with a separate /home next time around.

---

### Post by meindian523 on 2007-12-31
or you can burn your data to a CD/DVD-RW and keep it aside since you don't have a separate /home partition.

---

### Post by bapoumba on 2007-12-31
> **meindian523 said:**
> or you can burn your data to a CD/DVD-RW and keep it aside since you don't have a separate /home partition.
Yeah, that's what I call a removable support ^^
Can be a CD/DVD, usb drive etc. as long as it is not within the file system when reinstalling (can be some place over the network too).

---

### Post by Del Piero on 2007-12-31
Thanks guys, i backed up conky and the network files, i couldn't back up the home because it gave me errors even when i was using nautilus as root. Anyway it's upgrading now, i removed the nvidia drivers beryl the 3d party in the repo and heading toward feisty only to switch to gutsy. In worst case scenario i have the whole partition backed up. Thanks again guys.

---

### Post by bapoumba on 2007-12-31
> **Del Piero said:**
> Thanks guys, i backed up conky and the network files, i couldn't back up the home because it gave me errors even when i was using nautilus as root. Anyway it's upgrading now, i removed the nvidia drivers beryl the 3d party in the repo and heading toward feisty only to switch to gutsy. In worst case scenario i have the whole partition backed up. Thanks again guys.
Woot, keep us posted :)

---

### Post by meindian523 on 2007-12-31
So,that's all?You are upgrading through dist-upgrade rather than via clean install?Well,it's your choice,but please mark the thread solved.

---

