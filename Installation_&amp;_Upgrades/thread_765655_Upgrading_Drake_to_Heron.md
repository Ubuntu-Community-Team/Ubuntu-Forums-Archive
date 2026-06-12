---
title: "Upgrading Drake to Heron?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by phm on 2008-04-24
Hi,

I intend to try to upgrade Drake to Heron (though so far upgrading has never worked for me). However, the upgrade instructions are unclear to me at two points:

- The first step: "Make sure the "dapper-updates" software channel is enabled." That's probably perfectly clear for a developer who sees this terminology regularly, but I, hoping to do this only once every two years and using Ubuntu in a different languge, simply don't know the lingo. What am I supposed to do here, type- and click-wise?
- An installation, not from CD, would have a requirement of 256M memory for the installation process. Is this the same for an update, or does that have a different requirement? And either way, how do I find out from a running OS?

TIA,
                                                                      PHM

---

### Post by Pumalite on 2008-04-24
Remove all third parties from your /etc/apt/sources.list
System>Administration>Software Sources Enable update repos.

---

### Post by phm on 2008-04-24
Hi,

> **Pumalite said:**
> Remove all third parties from your /etc/apt/sources.list
OK, assuming that third parties mark their entries I should not have any problems with that.

> System>Administration>Software Sources Enable update repos.
Assuming I will be able to determine what menu choice is equivalent to  System>Administration>Software, what are Sources Enable updates repos? Menu choices, buttons, selectors?

PHM

---

### Post by rah1420 on 2008-04-24
phm, I'm with you.  I saw that first command and just sort of scratched my head.  Have to say, pumalite's response was less than helpful as well.  The apt-sources thing I can probably grok, but like you I don't have any menu options under System>Administration that resemble any permutation of "Software Sources Enable update repos."

I have, in order:
Device Manager
Disks
Language Support
Login Window
Networking
Network Tools
Printing 
Services
Shared Folders
Software Properties
Synaptic Package Manager
System Log
System Monitor
Time and Date
Update Manager
Users and Groups

I'm not a unix newbie but neither am I a sysadmin.  I do EDI and SAP for my day job so technology doesn't scare me.   However, the original upgrade advisory needs to be more fully explained.

---

### Post by phm on 2008-04-25
Hi,

I have a menu item called "Software" alright, but that's the submenu I created to group together all the programs to do with managing the software.

Obviously, the advice won't refer to that. However, I can't shake the feeling that the advice we've been given in this thread doesn't refer to any of the programs in the menu at all, and in fact would only work with a later version of Ubuntu.

BFN

---

### Post by Pumalite on 2008-04-25
Sorry:
System>Administration>Software Sources> Go to 'Updates' and enable them.

---

### Post by phm on 2008-04-25
Hi,

> **Pumalite said:**
> Sorry:
System>Administration>Software Sources> Go to 'Updates' and enable them.

Ah, thanks for explaining the "Software" bit. However, as can be seen from rah1420's list below, we do not have a menu item called "Software Sources".

OK, based on the translation of the help pop-up, my current theory is that we're supposed to choose "Software Properties", then select the tab "Internet-Updates", and tick the option "Automatically check for the availability of updates". (Names by approximation due to the language difference, but I rather doubt there will be "dapper-updates" of "software channel" in any of them.) The snag is that it's not really the "Automatically" part we're after, therefore, the descriptions don't match the option name very well.

Alternatively, and more in line with the original instruction, would be to use the first tab of the same program, and in the "channels" window make sure "Ubuntu 6.06 LTS updates" is ticked. Snag with this is that you'd expect the Ubuntu people to know what their own channels are called, but there could be a rather curious translation involved.

rah1420, if you can follow this, what does the latter say in English?

---

### Post by Pumalite on 2008-04-25
I'm posting from Hardy Heron. From 7.04 to now, there have been System>Administration>Sofware Sources. You enter your password and you can enable your repos: Third parties. Updates, etc

---

### Post by robbie75 on 2008-04-25
Hi everybody!

I upgraded my second notebook yesterday, just when the hardy upgrades wounded up :) and, guess what: on that notebook there was just an ancient Dapper Drake.
So don't be afraid, I simply started the upgrade process as explained on the ubuntu upgrade doc and everything went fine just out of the box and I didn't do anything except launching the upgrade from the update manager.
The update manager managed everything all alone, even the third party repository thing.

Now I'm enjoyng my Hardy Heron!

Have nice with the brand new Ubuntu! ;-)

---

### Post by phm on 2008-04-25
Hi,

> **Pumalite said:**
> ... From 7.04 to now, there have been System>Administration>Sofware Sources. You enter your password and you can enable your repos: Third parties. Updates, etc

Ah, dat explains why we can't find it: We're not on 7.04 or later; we're a year before that: 6.06.

Thanks for the elaboration. That would make it the second explanation:
In the menu select System>Administrator>Software Properties, then on the first tab, which translated as "Installation medium", make sure that in the "channels" window "Ubuntu 6.06 LTS updates" is ticked.

And either this translation of that channel name is very poor, or the Ubuntu people really don't know what their own channels are called. Weird.

Anyway, thanks for the explanation.

Would you also have any ideas about memory size requirements, or how to determine the amount of free memory space when your OS is running?

---

### Post by Pumalite on 2008-04-25
To run Hardy, you are going to need 340 MB of RAM minimum.
Talking about updates, have you tried?:
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

Change 'feisty' for whatever Dapper is called and 'gutsy' for hardy.

---

### Post by phm on 2008-04-25
Hi,

> **robbie75 said:**
> I upgraded my second notebook yesterday, just when the hardy upgrades wounded up :) and, guess what: on that notebook there was just an ancient Dapper Drake.

Do you have any idea about the amount of memory available on your laptop?

---

### Post by phm on 2008-04-25
Hi,

> **Pumalite said:**
> To run Hardy, you are going to need 340 MB of RAM minimum.

Are you sure? As it seemed to depend on the way the distribution was distributed, and considering the text then goes on about the installation I took [http://www.ubuntu.com/getubuntu/releasenotes/804]("http://www.ubuntu.com/getubuntu/releasenotes/804") to mean that amount of memory was needed to install it, rather than run. And then only for desktop installation from CD, where we're talking about updating from the Internet here.

> Talking about updates, have you tried?:
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

Change 'feisty' for whatever Dapper is called and 'gutsy' for hardy.

No. Is there a reason to do so? Does this do anything not covered by the update page?

(Drake is called "Dapper", that's why you're calling it that.)

---

### Post by Pumalite on 2008-04-25
Maybe the Server Edition needs less.

---

