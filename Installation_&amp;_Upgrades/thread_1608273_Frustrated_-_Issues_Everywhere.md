---
title: "Frustrated - Issues Everywhere"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by wiredniko on 2010-10-28
I am extremely frustrated with Ubuntu.

Using a 10.04 LTS installation disc, fresh are my install Firefox, multiple software, and the software updater thing did not work.

Figured maybe I messed something up.  I installed 10.04 LTS about 6 times from scratch, no other OS on the system.

They all had issues loading software, I click on whatever it goes to launch and nothing ever comes up.

I started doing updates through the command prompt using

sudo apt-get update
sudo apt-get upgrade

Then multiple packages broke.

Tried sudo apt-get -f install but I keep getting an error that openoffice and firefox fail their checksum.  

Click on upgrade by 10.10 version gives me the screen that says are you sure, with all the information for the distro and then brings up a window that says download 2 out of 2 and it also crashes.

So I figured alright, maybe the CD version I have is messed up.  I downloaded the 10.10 iso image and burned it three times.  Two of my live cds take me boot me to the purple ubuntu starting screen but nothing is displayed except for a little icon with a keyboard and the disabled person at the bottom.

Then my computer reboots...it does that continuously.

So scratch that as well.

So I say....WTF?

I am not sure what else I can do at this point, I have spent days trying to make this to work.

I am using AMD...so that means that I need the 64bit version right?

I really hope its something dumb that I will look back and think that I am an idiot.  Otherwise Ubuntu has totally failed me as a system.

---

### Post by mörgæs on 2010-10-28
If in doubt, always go for the 32 bit version, preferably the alternate one.

Also best is to check the CD's with MD5SUM before installing:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by wiredniko on 2010-10-29
I either do not have a x64 system or there was some another conflict somewhere.

I tried amd640-alternate and could not even get it to install.  Tried 386-alternate and it works like charm.

Thanks.

---

### Post by mörgæs on 2010-10-30
Good. Please mark the thread 'solved'.

---

