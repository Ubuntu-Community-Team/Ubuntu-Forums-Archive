---
title: "Converting mythbuntu to ubuntu server"
date: 2017-05-26
forum: Installation &amp; Upgrades
---

### Post by rykr on 2017-05-26
I have a mythbuntu 16.04 installation.  I am no longer using mythtv.   I'm wondering if I can move my installation to ubuntu server 17.04 by adding/removing packages rather than doing a new install?
Thanks!

---

### Post by oldfred on 2017-05-26
Do not know myth. 

But if you install server this is the app it uses to let you choose what type of server.

 Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel
sudo apt install ubuntu-server
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by deadflowr on 2017-05-27
> I'm wondering if I can move my installation to ubuntu server 17.04 by adding/removing packages rather than doing a new install?


I don't think moving from 16.04 to 17.04 for a server is good idea, and am quite confident I'm not alone in that notion.
However if it's something you feel strong about then it is possible, although, it can take a while to do.
To do so you will need to first make sure the system is set to be able to upgrade to the next release.
Run this simply liner to find out what state it's set at
```
grep Prompt= /etc/update-manager/release-upgrades
```
if it returns Prompt=normal, then it is set.
if it returns lts, then it needs to be changed.
To change either open that file
```
sudo nano /etc/update-manager/release-upgrades
```
and edit the Prompt line to read Prompt=normal,
or
run this one liner to change it
```
sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades
```
After you change it, if changing it was needed, you now need to run a full system update
```
sudo apt-get update
sudo apt-get upgrade
```
once that is done, now you can begin the release upgrade

To run the release upgrade run
```
do-release-upgrade
```
and follow what directions come as they come. You will probably be prompted a few times throughout on needing to decide about various updated config files.
The system will hang at any prompt until you make a selection of the choices it wants you to make, 
unless you've got a lot of personalized config files most choices (if any) to take when prompted will be the default.

Now understand that this is only part one. as the release upgrader only upgrades to either the latest supported release or to the next long term supported release.
So from 16.04 the next supported release is 16.10, which is what you will be upgrading to.
To get to 17.-04 from 16.10, you should only need to rerun the do-release-upgrade command once more.
And that should do it.



As to why moving from 16.04 to 17.04 isn't the greatest of ideas is two reasons.
First, 17.04 is a normal release and only gets a short 9 month window of support, meaning that you will need to upgrade the system all over again in a short time.
(16.04 is a long term support release and gets 5 years of support)

Second is that while release upgrades are generally safe, things can happen that can be irrevocable and doing two release upgrades can only stretch the odds of something not wanted happening.

And in the event that you decide to just do a fresh install, reason number one stills applies.

Well that's my two cents as to how you can upgrade from 16.04 to 17.04 and why you probably shouldn't.
The call is yours.
Good luck, in whatever way you decide to go.

---

