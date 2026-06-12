---
title: "beryl-manager lost after upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2007-04-20
unlike many, I have upgraded and all seems to have gone well apart from beryl-manager is now missing. how do I get it back ???

---

### Post by rich.bradshaw on 2007-04-20
check it's installed:

sudo apt-get update
sudo apt-get install beryl emerald

if it is:

beryl-manager

That should work...

---

### Post by celticbhoy on 2007-04-20
beryl is installed ok as it is still running.

Just the manager part that is no longer there.

---

### Post by TmP on 2007-04-20
Same here.

It seems that its running but does not show up on the top bar

---

### Post by GeDaMo on 2007-04-20
Make sure the beryl-manager package is installed as well as beryl

---

### Post by TmP on 2007-04-20
yes it is!

When I load it, it just goes into sleep mode...

I can run beryl ok with the "beryl" command
when I try to run beryl-manager I get kicked out of beryl:

Reloading options
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by TmP on 2007-04-21
I think I will back out of the Feisty for a few weeks.
Hope the issues are fixed when I return

---

### Post by Crosbie on 2007-04-21
Have you gone through the [installation instructions for Feisty/Beryl ]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_7.04_.28Feisty_Fawn.29")at the Beryl Wiki?

I found there were some differences and tweaks that needed to be  worked through before my Beryl setup worked again as it should.

---

### Post by celticbhoy on 2007-04-21
just going to check it out. have looked at my setup and the only repo's that aint feisty and are still stuck with edgy are tuxfamily where I get latest beryl svn from (I think). Dont know if that is root of prob after upgrade !!

---

### Post by celticbhoy on 2007-04-21
just had a go. still no joy.

seems the problem has to do with beryl-settings.

get this after sudo apt-get update beryl beryl-manager

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  beryl: Depends: beryl-settings but it is not going to be installed
E: Broken packages


Anyone had this, and know how to sort it???

---

### Post by bulldog on 2007-04-21
Repair the broken packages first with synaptic and try again.
I have Feisty **and** Beryl up and running from Herd 4,but I did a clean install,not an upgrade.

Upgrading is best without any 'strange' application installed,only applications which came from the official ubuntu repositories will be upgraded.

---

### Post by celticbhoy on 2007-04-21
I have had a go. 

When I select beryl, or beryl manager they state that they require beryl-settings and it wont be installed.

Beryl-settings says it requires beryl-settings-bindings, and that that will not be installed.

Beryl-settings-bindings says that it Depends: python (<2.5) but 2.5.1~rc1-0ubuntu3 is to be installed.
How do i get out of this ???

---

### Post by celticbhoy on 2007-04-21
As I am guessing that the problem is that the settings-bindings package requires a version of python before 2.5 other people must have this prob, or can I becktrack my python to version before 2.5

---

### Post by celticbhoy on 2007-04-21
just checked synaptic and python 2.4 & 2.5 loaded. If I try to remove 2.5 it want to also remove all other software I have loaded which uses python, even though 2.4 still there

---

### Post by bulldog on 2007-04-21
Try to remove Beryl and emerald and all the settings you have made.
Reinstall the package when done and see if this work.

---

### Post by celticbhoy on 2007-04-21
I have un-installed beryl and re-installed without the tuxfamily repos, and I now have a working setup with beryl-manager working. BUT I am back to 0.2.0 rc3 instead of SVN which means that I no longer have the beryl screensaver. If anyone can get SVN working with all dependencies and beryl-manager please let me know how-to.

---

