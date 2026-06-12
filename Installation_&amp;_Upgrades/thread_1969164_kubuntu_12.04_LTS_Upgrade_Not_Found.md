---
title: "kubuntu 12.04 LTS Upgrade Not Found"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by mrcpuhead on 2012-04-29
I've trying to upgrade from Kubuntu 10.04 LTS (64-bit) to 12.04 LTS, and Kpackagekit doesn't find the upgrade no matter what source options I choose.  Any help? :confused:

---

### Post by mrcpuhead on 2012-05-01
> **mrcpuhead said:**
> I've trying to upgrade from Kubuntu 10.04 LTS (64-bit) to 12.04 LTS, and Kpackagekit doesn't find the upgrade no matter what source options I choose. Any help? :confused:
 
UPDATE:  I noticed the GUI showed the full upgrade command line, so I tried running that from a terminal, and lo and behold, that did the trick!  Still waiting for the upgrade to complete, as I didn't realize it prompts in a few places, and had to leave for work before the package installs completed. :guitar:

---

### Post by bakta on 2012-05-02
I have encountered exactly the same problem. But I can't find the full upgrade command line, you're mentioning. Can you kick me a bit, please?

---

### Post by drmrgd on 2012-05-02
> **bakta said:**
> I have encountered exactly the same problem. But I can't find the full upgrade command line, you're mentioning. Can you kick me a bit, please?

You should be able to run the upgrade from terminal by running:

```
sudo do-release-upgrade
```

If you get a message that there are no newer versions available, double check your notifications for new system versions (which got me the first time I tried to upgrade).

Hope that helps!

---

### Post by jadtech on 2012-05-02
the upgrade documentation I have read  tells you that you have to have all current updates before the release upgrade will show up to upgrade from version 10.04 .. 

you have to be fully up to date version 10.04.4 before you will be able to trigger the current release ..

---

### Post by frijj2k on 2012-05-02
I'm running Kubuntu 11.10..

I am fully up-to date and have rebooted. There are no new upgrades to install (checked).

The distribution upgrade notification is not appearing and if I run 'sudo do-release-upgrade' and get the message 'No new release found'  :(

Any ideas?

---

### Post by bakta on 2012-05-03
Ok. It seems, something strange is happening there. I'll try to describe more precisely

I have my PC with kubuntu 10.04LTS. First I wanted stable system and had not enough time at the beginning to fix broken things after each upgrade and 10.04 was still good enough and updated. I could use it quite well. So I decided to wait for next LTS (this one) with the update.

Now I have fully updated 10.04, which is working fine.
I can even see in the /var/lib/update-manager/meta-release record for all the releases including 12.04LTS.
When I switch Release upgrade option in the Software sources from LTS only to Normal Releases I can see available update for 10.10.
When I switch back to LTS, no update is shown.
do-release-upgrade says: Checking for a new ubuntu release and then: No new release found

I don't know, what cache, config, package infos got messed. This thread seemed to show way, how to force this update (run it from command line), regardless KPackageKit says.

I probably could do it one by one upgrade from 10.04->10.10->11.04->11.10->12.04, but that is not the way I'd like to follow.

Any ideas? I'm not so familiar with these modern "click and pray" features. I have updated my debian from 5 to 6 just by editing sources.list and then apt-get ... One never knows what might get broken if changed lower level stuff manually.

---

### Post by LiquorAndelixir on 2012-05-04
I've found I'm seeing exactly the same problem, no LTS upgrade available. 

This is happening on both my main Kubuntu desktop, and also on my Xubuntu systems - (one is a server setup on an EEEBox, the other is a netbook).

 I'm unsure if it's safe to try and go ahead with the workaround below. Does anyone know if what I'm doing (apart from cancelling the install, that is) is likely to cause an problems or fail?

 Just using the 'do-release-upgrade' as a bare line to itself as shown above, I get the 'No new release found' message.  Using the command line I saw in the release notes from [https://help.ubuntu.com/community/PreciseUpgrades/Kubuntu/10.04LTS](https://help.ubuntu.com/community/PreciseUpgrades/Kubuntu/10.04LTS), and as shown below, I get the following errors, after which I cancelled out of the dialog box where it asks me if I want to 'start upgrade' (with about 2GB of files to download).

[FONT=Lucida Console]liquor@Linux-W15:~$ sudo do-release-upgrade -m desktop -f kde -d
[sudo] password for liquor: 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
extracting 'precise.tar.gz'
can't load kde (No module named kde)
can't load DistUpgradeViewGtk (No module named vte)
can't load DistUpgradeViewGtk3 (No module named gi)
Error: "/var/tmp/kdecache-liquor" is owned by uid 1000 instead of uid 0.
adept_manager: no process found
adept_updater: no process found
exitMainLoop
WARNING: Failed to read mirror file
can't load kde (No module named kde)
can't load DistUpgradeViewGtk (No module named vte)
can't load DistUpgradeViewGtk3 (No module named gi)
Error: "/var/tmp/kdecache-liquor" is owned by uid 1000 instead of uid 0.
adept_manager: no process found
adept_updater: no process found
exitMainLoop
WARNING: Failed to read mirror file[/FONT]

---

### Post by frijj2k on 2012-05-04
I had already tried "sudo do-release-upgrade -m desktop -f kde -d" as well but still get the same "No new release found" message...

I have tried this on 2 two different machines... both running Kubuntu 11.10 and fully up to date.

---

### Post by westie457 on 2012-05-04
Try this from this post 
[http://ubuntuforums.org/showpost.php?p=11893873&postcount=2](http://ubuntuforums.org/showpost.php?p=11893873&postcount=2)


Remember to change the 'oneiric' to whatever your current release is.
> 1. This command is used to auto edit the sources.list file on an install of Oneiric Ocelot and could be considered as a first step to converting to Precise Pangolin. However this and other commands may be moot after Alpha .iso are released. You can still play it safe and test the kernels but breakage may occur nonetheless.
Code:
     sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
2. This command will update your repositories to PP.
Code:
     sudo apt-get update && sudo apt-get dist-upgrade
3.This command is inclusive in #2. but is always good to run after removing or purging stuff.
Code:
     sudo apt-get update
4.This command is also included in #2. and upgrades any new files that are set in the repositories.
Code:
     sudo apt-get upgrade

Hopefully it will work for you.

---

### Post by bakta on 2012-05-05
Thank you guys.
I have read the page about upgrade and didn't notice that line in the picture.
The -d switch probably does the trick - for me as I'm at 10.04.4 now.

Also the method with lower level commands (apt-get) is very nice.

The do-release-upgrade with switches is working for me. Thank you.

---

### Post by pcarbonell on 2012-05-08
According to PP Release Notes:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS")

> Upgrading from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS

It is generally recommended that users of Ubuntu 10.04 LTS [B]wait until the first point release, due in July, before upgrading.
[/B]
To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure.

[LIST=1]
[*]Start System/Administration/Software Sources
[*]    On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
[*]    Press Alt-F2 and type update-manager -d
       [LIST=1]
[*]Click the Check button to check for new updates. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
[*]        A message will appear informing you of the availability of the new release. Click Upgrade.
    [/LIST]
Follow the on-screen instructions.[/LIST]

So until July the update manager won't show the upgrade to 12.04 option. 
If you can't wait, and as replied before, the do-release-upgrade with switches will do the job.

---

### Post by mrcpuhead on 2012-05-13
> **bakta said:**
> I have encountered exactly the same problem. But I can't find the full upgrade command line, you're mentioning. Can you kick me a bit, please?

I was able to successfully run the upgrade via 

**sudo do-release-upgrade -m desktop -f kde -d**

Curiously, even though I was upgrading from kubuntu (KDE desktop), when the upgrade finished, it had switched me back to the ubuntu unity desktop.  A colleague tells me that's intentional, to try to get users onto the unity desktop...Argh!:frown:

---

