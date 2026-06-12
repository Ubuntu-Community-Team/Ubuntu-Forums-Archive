---
title: "No upgrade option in Update Manager"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by jamesjai on 2010-05-01
Dear all,

I am using Ubuntu 9.10, I want to upgrade to Ubuntu 10.04. I followed the steps mention in Ubuntu web site but my update manager is not showing any upgrade option.

I tried below command that too did not show any output about the available updates, 

"do-release-upgrade"
Checking for a new Ubuntu release
No new release found

Please help me... I am egar to upgrade to Ubuntu Lucid, LT 10.04....

Thank you.

Best regards...

---

### Post by The Thunder Chimp on 2010-05-01
Try pressing Alt-F2. In the run box, type in "update-manager -d". That could work. Tell me if it did.

---

### Post by jamesjai on 2010-05-01
I've done it all.

update-manager -d
apt-get dist-upgrade

By terminal and by alt-f2.

Still I cant get upgrade option in my update manager..

Please help...

---

### Post by SoFl W on 2010-05-01
What is displayed when you type 
```
lsb_release -a && uname -r
```in terminal?

---

### Post by jamesjai on 2010-05-01
lsb_release -a && uname -r says,

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
2.6.31-21-generic

---

### Post by The Thunder Chimp on 2010-05-01
You could perhaps try to upgrade from CD. I heard you could do that. Burn a 10.04 CD (your architecture) and try upgrading from that.

---

### Post by ssulaco on 2010-05-01
Have you checked software sources,updates tab....at the bottom, tick (show new dist releases) "normal releases"

to find softwaresources,go sys -> admin ->  software sources

---

### Post by jamesjai on 2010-05-02
I tried all the options in update manger, but still no upgrade message appear.

Please solve this problem...

Thanks

---

### Post by shriramrs31 on 2010-05-04
I have the same problem. Initially I thought that there was some kind of a delay in offering updates to 9.10 computers, but now I know that this is an issue.

I tried all the options in the settings and starting with update-manager -d and even with synaptic. none of them shows any distribution updates.

I am using 9.10 with the latest offered kernel and all the packages updated as of today. I also have KDE, GNOME and XFCE installed.

Other than the option of downloading and installing from the CD image, can anyone help me with the automatic upgrade option ?

Thanks.

---

### Post by beercoder on 2010-05-04
I'm also facing the same problem. I'm on 9.10 and have not updates to apply. I've two installs of Ubuntu - one at home (direct internet connection) and one at office (via proxy, behind firewall). 

At home, I was able to upgrade without any problem. But at office, I just do not see the upgrade button and message in Update Manager. I'm connected to internet and its wide open to download all. Any updates for 9.10 mentioned in Update Manager, I was able to download and install.

It would be great if somebody can help resolve this problem

Cheers !!!
- BC

---

### Post by shriramrs31 on 2010-05-04
Hmmm I am also behind a proxy and firewall at work. The proxy settings along with the authentication information are all set properly and I have been doing normal package updates without any problems till date.

Can this proxy be an issue somehow for fetching distribution upgrades ?

---

### Post by bbbaldie on 2010-05-04
> **shriramrs31 said:**
> 
Can this proxy be an issue somehow for fetching distribution upgrades ?

Absolutely! I hard-coded a pass-through address my network admin gave me and updated. Still no upgrade option. Turned off proxy in Firefox and system-wide under preferences/network proxy. THEN, I remembered taht **Synaptic has its own proxy setting**. Turned it off there, ran update manager, and **THERE WAS THE UPGRADE TO 10.04 OPTION!** 

Hope this works for all of you. :P

---

### Post by shriramrs31 on 2010-05-04
Thanks bbbaldie. This seems definitely the reason. I dont know if it is possible for me to bypass the proxy after talking with admin, but atleast I can do the updates at home, where there is no proxy setting. This is definitely the workaround now to update my system.

But this would not be the right solution. I think when I am able to get the normal security / latest updates via proxy; the distribution updates should also pass through proxy. My first guess would be something to do with port numbers. Does anyone know more details about this ? I am sure there must be a way to correct this and do distribution upgrade also through proxy.

---

### Post by beercoder on 2010-05-04
Without proxy, it works like a charm... but no admin will open the internet wide open in company to upgrade the system. 

There must me someway to upgrade using proxy. 

Where are all Ubuntu Gurus? :confused: Please help this poor soul...

---

### Post by pgmer6809 on 2010-05-07
I had the same issue. The reason is that you probably do not have the correct option checked to cause update manager to do this.

Go to System=>Administration=>SOftware Sources.
Click on the Updates Tab.
At the bottom you will see a box that says: 
Long Term support releases only. (Or never).

Change this to:
Normal Releases

Restart Update Manager if it is still running and you will see an option to upgrade to the next release.
In my case it gives me the option of upgrading from 8.04 (Hardy) to 8.10 (Ibex)
This is not what I want of course. I want to upgrade to the next LTS release, so I changed the option back to LTS releases again, and the upgrade option in Update Manager goes away.

---

### Post by beercoder on 2010-05-07
> **pgmer6809 said:**
> I had the same issue. The reason is that you probably do not have the correct option checked to cause update manager to do this.

Go to System=>Administration=>SOftware Sources.
Click on the Updates Tab.
At the bottom you will see a box that says: 
Long Term support releases only. (Or never).

Change this to:
Normal Releases

Restart Update Manager if it is still running and you will see an option to upgrade to the next release.
In my case it gives me the option of upgrading from 8.04 (Hardy) to 8.10 (Ibex)
This is not what I want of course. I want to upgrade to the next LTS release, so I changed the option back to LTS releases again, and the upgrade option in Update Manager goes away.
This even does not work. Changes which you are mentioning and worked for you... did it work when you connect through proxy?

Cheers !!!
- BeerCoder

---

### Post by vedavrata on 2010-05-13
> **jamesjai said:**
>  I am using Ubuntu 9.10, I want to upgrade to Ubuntu 10.04. 

"[FONT="Lucida Console"]**do-release-upgrade**[/FONT]"
Checking for a new Ubuntu release
No new release found 

Check the file '**[FONT="Lucida Console"]/etc/lsb-release[/FONT]**'

Or  **lsb_release -a**

---

### Post by EricDP on 2010-05-22
I had this problem too. In update manager under "Settings", "Ubuntu Software" tab, "Download From", I changed it from "Canada" to "Main Server" and the upgrade appeared. Maybe a problem on some mirrors?

---

### Post by sundoulos on 2010-06-07
Ok, so I'm on Kubuntu 10.04 and my Updates page doesn't look like the screenshot attached to post #7. The two lines - Release Upgrade and Show distribution releases is not there. Synaptic is version 0.63.1, Adept is version 3.0 Beta 7, Add & Remove Software is version 0.5.4.

How do I make it show up?

---

### Post by guimaster on 2010-11-05
> **pgmer6809 said:**
> I had the same issue. The reason is that you probably do not have the correct option checked to cause update manager to do this.

Go to System=>Administration=>SOftware Sources.
Click on the Updates Tab.
At the bottom you will see a box that says: 
Long Term support releases only. (Or never).

Change this to:
Normal Releases

Restart Update Manager if it is still running and you will see an option to upgrade to the next release.
In my case it gives me the option of upgrading from 8.04 (Hardy) to 8.10 (Ibex)
This is not what I want of course. I want to upgrade to the next LTS release, so I changed the option back to LTS releases again, and the upgrade option in Update Manager goes away.

 This worked for me.

 I love Ubuntu but these little bugs frustrate me.

 GuiMasTER

---

### Post by beercoder on 2010-11-13
Check this post for the solution for upgrading sitting behind proxy.

[http://jaykhimani.blogspot.com/2010/11/upgrading-ubuntu-to-new-release-behind.html](http://jaykhimani.blogspot.com/2010/11/upgrading-ubuntu-to-new-release-behind.html)

Cheers !!!
- BC

---

### Post by Innigo on 2011-01-27
+1 here. I have the same problem.  On one machine I'm still stuck. On the other one I managed to coax it into upgrading. I made some notes:
Update-Manager doesn't detect that a distribution upgrade is available. 

* tried changing /etc/apt/sources.list both manually and repeatedly in Synaptic

* changed /etc/update-manager/release-upgrades from 
prompt=lts to normal and back to lts

* tried sudo do-release-upgrade -- still no good

* checked /var/lib/update-manager/meta-release for missing section as per workaround at [https://help.ubuntu.com/community/UpgradeProblems](https://help.ubuntu.com/community/UpgradeProblems)

* on Other Software tab I unchecked two Canonical entries 
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (source)

It was then I got the msg. "Repositories Changed you need to reload" (list of packages in Synaptic) This msg had previously preceded the brief appearnage of the msg that there was a release upgrade available but I'd put it off  because I wanted to follow the advice at :
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)  and at 
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

* Incidentally, I also selected the main server instead of my national mirror which I suspect just slowed me down. Whatever the case, after more downloading and reading of package info, I hit [Check] again and Voila!

"New Ubuntu relase 10.04.1 LTS available"
Hurrah!
It went ok and after restarting, I still had all my files in my home :-)
++++++++++++

Why this doesn't work for my other machine, I don't know. The problem seems to be a bit like an intermittent electrical fault. It either has many causes or it's a bit random for some reason.

From what I've gathered, things like do-release-upgrade and changing settings in Update Manager or editing files underlying it may successfully trigger an attempt reload new upgrades but if it's not fully up to date and ready to go or if some other little things...? somewhere...? are not quite right, the upgrade is not offered. 

The problems seem to be continuing with 10.10 in slightly different form but with similar symptoms. If anyone could pin down the main cause(s) of this problem, it would be really great.

:popcorn:

---

