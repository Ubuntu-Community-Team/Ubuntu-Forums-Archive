---
title: "Request some advice &amp; help as 16.04 LTS to 18.04 LTS upgrade failure"
date: 2018-10-24
forum: Installation &amp; Upgrades
---

### Post by calif99x on 2018-10-24
Hi:

I have been searching the forum to see if this is an existing thread, please point or redirect as applicable.

Problem:
I got the note that 16.04 LTS Desktop 64 bit was reaching EOS, so I accepted the prompt to upgrade to 18.04 LTS.  I figured WTH, I have boot setup on a 512GB SSD and worst case I will just have to wipe that drive and do a fresh install.

The upgrade seemed to chug along, and then failed with some vague error message about installing the OS not on the SSD, but on a different HD.  Obviously I should have paid more attention to the install setup messages to confirm the install was going to the SSD :-(.  It appears as part of the failure, the boot loader was either disabled or wiped out.

I thought I would deal with the situation by burning a 18.04 LTS CD, and rerunning the install.  The install failed, and the boot loader was not installed.

So, I am stuck with a system that will not upgrade, will not boot from the SSD or the HD, and I may have lost a HD worth of data.  I can bring the system up using the live CD, but not much progress past that.

Any guidance on how to recovery my system?

Thanks
sk

---

### Post by TheFu on 2018-10-24
If you run Boot Repair from a flash drive (or that DVD you made), there's a *gather info* choice at the bottom. Run that and post the URL it makes here.  URL, not all the output, please.  You'll need to install the tool first. This will provide needed facts to be able to help better.

FYI, 16.04 LTS Desktop (Unity) has support until 2021. All mainline LTS Ubuntu distros have 5 yrs of support, including Ubuntu Server.

Some packages you might have installed may have already lost support, but that is the situation for some packages the day we install them.  There is absolutely NO HURRY to move from 16.04 to 18.04 for most people.  Even the less supported DE releases have 3 yrs of support, so you have until 2019 Apr or July.

It is always a very good idea, I consider it mandatory, to have a know-I-can-restore backup, before doing any major updates and definitely before doing a release upgrade.  If you have that, you can restore the 16.04 system and wait.  

Whenever installing a new OS, I find it best to only have 1 storage device connected. This prevents the installer and boot tools from becoming confused.  It also means I won't accidentally trash my data on all the other disks.  If you read these forums for any time, you'll see a few people who destroyed lots of data by accidentally pointing the install at the wrong storage.  Ouch.  For people uncertain about storage device names and partitioning, it is easy to get the wrong device.

Anyway, hope this is helpful on some level.

---

### Post by calif99x on 2018-11-03
OK, had to find some free time.

URL is [http://paste.ubuntu.com/p/Vy6tSyNnQq/](http://paste.ubuntu.com/p/Vy6tSyNnQq/)

Thanks

Addendum; I got a bit frustrated and tried the install again.  I unplugged all the drives except for the SSD and selected the option to erase the drive and do the install.

The install seemed to finish correctly, I got the message to remove the media and restart the system to finish the install.

Restarting, the Ubuntu logo came up, but the five dots that change colors to show boot progress showed no changes.  The system just sat there for 15 minutes, then I tried restarting it, stopped at the same spot again.

I might have to go back to 16.04 as it looks like this release is borked.

---

