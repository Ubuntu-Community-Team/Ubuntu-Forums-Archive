---
title: "How to uninstall Firefox 3 Beta and install non-beta version?"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by jacob85 on 2008-07-12
Yesterday, i installed Ubuntu 8.04 LTS and it has Firefox 3 Beta 5. But i want to use new proper version of Firefox. 
How can i do this?

---

### Post by SkonesMickLoud on 2008-07-12
In a terminal window, paste the following:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

This will update Firefox as well as all other outdated packages on your system.

---

### Post by jacob85 on 2008-07-12
thanks but i just want firefox. i don't want other updates.

---

### Post by SkonesMickLoud on 2008-07-12
In that case, go to System >> Admin >> Update Manager, and uncheck everything but Firefox.

---

### Post by Dale61 on 2008-07-12
Re: the poll question.

Did what worked?

---

### Post by orclev on 2008-08-08
Just tried it out and it didn't work for me. It looks like beta 5 is the latest version in the Ubuntu repositories. I just downloaded 3.0.1 from Mozilla directly, and I'm going to see how a "manual" upgrade fares. Would be nice if Ubuntu updated their repositories though, as 3.0.0b5 is quite out of date at this point (I'm updating myself because FF keeps locking up on certain pages).

---

### Post by aysiu on 2008-08-08
Can you paste these commands in the terminal and then paste the output back here? ```
cat /etc/apt/sources.list
cat /etc/lsb-release
ls -l /usr/bin/firefox
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by Dale61 on 2008-08-08
> **orclev said:**
> Just tried it out and it didn't work for me. It looks like beta 5 is the latest version in the Ubuntu repositories. I just downloaded 3.0.1 from Mozilla directly, and I'm going to see how a "manual" upgrade fares. Would be nice if Ubuntu updated their repositories though, as 3.0.0b5 is quite out of date at this point (I'm updating myself because FF keeps locking up on certain pages).

I have FF 3.0.1, which was downloaded from the repo's.  I did a manual download / install of FF2, and had heaps of problems, but have been trouble free with the repo downloaded FF 3.0.1.

---

### Post by SkonesMickLoud on 2008-08-09
> **orclev said:**
> Just tried it out and it didn't work for me. It looks like beta 5 is the latest version in the Ubuntu repositories. I just downloaded 3.0.1 from Mozilla directly, and I'm going to see how a "manual" upgrade fares. Would be nice if Ubuntu updated their repositories though, as 3.0.0b5 is quite out of date at this point (I'm updating myself because FF keeps locking up on certain pages).

Do you have all repo's enabled?

Before you update, run:

```
sudo aptitude update
```

And yes, I know that Update Manager does this, but it doesn't hurt to make sure.

---

### Post by sandysandy on 2008-08-09
>  sudo apt-get install firefox  works

it will get u version 3.01 as of now

regards

---

### Post by Bearna on 2008-09-09
Hi 
I have exactly this issue. But on following the instructions below I am told I have the most up to date version of firefox. The firefox version installed is the Firefox 3 Beta 5
Details as follows
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008041514 Firefox/3.0b5

Has anyone encountered this issue

Thanks

---

### Post by SkonesMickLoud on 2008-09-09
> **Bearna said:**
> Hi 
I have exactly this issue. But on following the instructions below I am told I have the most up to date version of firefox. The firefox version installed is the Firefox 3 Beta 5
Details as follows
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008041514 Firefox/3.0b5

Has anyone encountered this issue

Thanks

Might try uninstalling/reinstalling.

First, you'll want to back up your ~/.mozilla folder:

```
cp ~/.mozilla ~/.mozilla.back
```

Close all instances of Firefox and don't start them until after the reinstall.

Then, fire up Synaptic, search for Firefox, select "Mark for Complete Removal", click apply.  Then, click "Reload".  Now, find Firefox again.  Make sure the column titled "Latest Version" reads 3.0.1.  Mark for install, click apply.  Start FF3.

---

### Post by Bearna on 2008-09-09
Hi there
Thanks for the reply. No success I am afraid. I followed your directions but the only version available for install was the beta version again. I continued with the install and got the following version reference

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008041514 Firefox/3.0b5

Is there something I am missing or soemthing else I could try?

Thanks in advance

---

### Post by cariboo on 2008-09-09
You may have to update your sources list before you can install firefox 3. IF it is saying that Firefox 3.0b5 is the latest release version. In a terminal type:

```
sudo apt-get update
```

Then

```
sudo apt-get installl firefox
```

Jim

---

### Post by Bearna on 2008-09-10
Hi guys
Still no luck I am afraid. I got the following message when I followed the above instructions

sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Any suggestions would be appreciated

Thanks

---

### Post by Bearna on 2008-10-31
Hi folks
Maybe I have stumbled on the solution inadvertently here myself. In attempting the upgrade to 8.10 I note from the upgrade instructions to go to start/administration/software sources. When there check the tab for upgrades and click on the butoons for important security upgrades and recommended upgrades. Details are shown here - [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Both of these had defaulted to not being ticked for me in 8.04. By completing this I checked for upgrades and got notifiied of over 360 upgrades outstanding! One of these was Firefox beta to the latest release. Clicking install upgrades without upgrading completed the trick.

---

