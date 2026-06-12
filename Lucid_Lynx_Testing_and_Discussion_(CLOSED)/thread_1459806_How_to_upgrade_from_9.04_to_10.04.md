---
title: "How to upgrade from 9.04 to 10.04?"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RamR on 2010-04-21
I want to upgrade from 9.04 to 10.04 and would like to get some advice on how to do this.  I have read some things about file systems and also the possible inability to do the upgrade from the update manager.  Unfortunately I have been more confused than anything.  

Any help would be appreciated.  Also, can I upgrade to the RC or should I wait a week?

Thanks in advance.

---

### Post by Didius Falco on 2010-04-21
You won't be able to upgrade directly from 9.04 to 10.04. 

What you could  is to download the alternate install .iso for 9.10 and do the following:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) - look for the "text-based installer" link on this page

1. Mount the downloaded ISO image in the CD drive mounting point by typing the following:
     ```
 sudo mount -t iso9660 ubuntu-9.10-alternate-i386.iso /cdrom -o loop
```   2. Run the upgrading application found on the CD.
      ```
gksu "sh /cdrom/cdromupgrade"
```   3. The machine will now upgrade and eventually reboot. You may now remove the CD entry to the image found in the file: ```
/etc/apt/sources.list
```This will upgrade you to 9.10. From there you can do the update to 10.04.

Lucid makes a lot of changes. If you have the room on your HD, I'd really recommend installing it to a separate partition to test it out.

I have an upgraded install (from 8.04 forward, no less) and it's much more bloated and slower than my  fresh install. One thing I can point out right away is the boot time. On the upgraded install, it's booting in 30-24s on average. On the fresh install, it's 15-18 seconds.

It's just all around snappier and more responsive than my old install, and it's easy to import your email, bookmarks, etc., to get your important settings back.

BTW, at this stage, I'd just wait for the official release unless you want to help out in the final phase of testing. Especially, if you go the Upgrade to 9.10 route - that would give you the time to test out everything in 9.10 and resolve any issues you might have there first. 

I hope this helps!

Regards,

Didius


That's my .02...

---

### Post by RamR on 2010-04-22
Thanks for the quick reply.  Another question comes to mind.  If I wait a week for the final version will I be able to do a clean install without any problems or extra steps?

---

### Post by RickyCodes on 2010-04-22
id go with a new install 

just installed the latest amd64 iso alternate 20100419.1 and it went with out a hitch. 

after the install I updated the nvidia drivers and that also went with out a hitch.

After that I installed a printer that has been giving me troubles in beta1 and that worked on the first attempt. 

So far gtg on this install. but if you want to be 100% sure wait until the final

---

### Post by Longinus00 on 2010-04-22
> **Didius Falco said:**
> 
That's my .02...

Is all that really necessary? Is it no longer possible to upgrade from 9.04 to 9.10 via update-manager?

---

### Post by Artemis3 on 2010-04-22
Yes, upgrade to 9.10 and then to 10.04. I did it just fine.

---

### Post by Didius Falco on 2010-04-22
> **Longinus00 said:**
> Is all that really necessary? Is it no longer possible to upgrade from 9.04 to 9.10 via update-manager?

It's not required, but it's a lot faster than using the Update Manager, and you don't have any worries about failed downloads.

I've done it both ways, and I found the iso way much less time-consuming.  Besides, it's just basically a 1-2-3 process: d/l the iso, mount the iso, upgrade from the iso. One download and two Terminal commands hardly seems like "all that", to me anyway.

To use the Update Manager, you'd have to do not one, but two upgrades. The only way to skip over releases is from LTS to LTS.

---

### Post by Didius Falco on 2010-04-22
> **RamR said:**
> Thanks for the quick reply.  Another question comes to mind.  If I wait a week for the final version will I be able to do a clean install without any problems or extra steps?

For a fresh install, yep, you could even do it with the RC candidate that will be released some time tomorrow. I'd wait, though, so you'll have a bootable Live cd of the final release - you've waited this long, what's another week?

---

### Post by uRock on 2010-04-22
Instead of taking 4-6 hours to run two upgrades, I'd recommend doing a clean install. At least with doing a clean install you can first run the LiveCD and make sure everything is compatible.

---

### Post by manoynmonic on 2010-04-22
> **Didius Falco said:**
> For a fresh install, yep, you could even do it with the RC candidate that will be released some time tomorrow. I'd wait, though, so you'll have a bootable Live cd of the final release - you've waited this long, what's another week?

Listen to this one ^.  He speaks wisdom.

---

### Post by d3v1150m471c on 2010-04-22
backup your files and use a live cd. anything else often ends in disaster.

---

### Post by RamR on 2010-04-22
Thanks... The one week countdown begins then.

---

### Post by ranch hand on 2010-04-22
Good plan.

A clean install will also avoid the problems with moving from grub-legacy to grub2.

If you, at some point, do decide you upgrade I would purge grub and grub common from 9.04.  Check to make sure all files are gone (particularly /boot/grub/menu.lst) and then install grub-pc and grub-common from the juanty repo (grub1.68).

The upgrade, other wise, leaves you with half one and half the other grub and it will eventually become unstable.  It has caused a lot of problems.  This is not the fault of either grub version.  It is just a stupid way of changing versions.

---

### Post by beerem on 2010-04-22
I would recommend that you take out your existing drive and put in a new drive, install the new version and then add in the old drive, copying files across. This way when things go horribly wrong, you can go back to how things were.

I have personally found that upgrading to 9.10 was always a disaster and have now gone back to 9.04 where everything works.

I shall watch with interest on your conclusions with 10.04

---

### Post by uRock on 2010-04-22
> **beerem said:**
> I would recommend that you take out your existing drive and put in a new drive, install the new version and then add in the old drive, copying files across. This way when things go horribly wrong, you can go back to how things were.

I have personally found that upgrading to 9.10 was always a disaster and have now gone back to 9.04 where everything works.

I shall watch with interest on your conclusions with 10.04

That is what the /home partition is for. It is also good to create a .txt with all programs you have installed so that you can make one command to install them all after the clean install such as "sudo apt-get install bacon egg cheese toast coffee-beer"  just replace breakfast with program names with one space between each.:P With this command set aside it would be really easy to go back to the previous install.

---

### Post by ranch hand on 2010-04-22
The package debfoster will create just such a list for you.

---

### Post by nanog on 2010-04-22
The OP did not ask about the best way to do a fresh install. 

Ubuntu supports upgrades. The frequent advice to not perform upgrades on  these forums does not help make Ubuntu better (and is often kind of annoying).


An example of why upgrades are often essential:
I have a box with several programming environments and hundreds of applications installed. The vast majority of these are not installable via an apt command even though most are open source. The box has dozens of user accounts and complex configs for nfs/samba. A fresh install would take weeks to reconfigure.

Another example:
I've spent many hours tweaking ubuntu and do not want to constantly reinstall every 6 months. In fact, this is one of th main reasons why I stopped using windows and moved to linux 8 years ago.

---

### Post by nanog on 2010-04-22
> A clean install will also avoid the problems with moving from  grub-legacy to grub2.Upgrading does not convert grub legacy to grub. Upgrades are designed to be SAFE. 


This laptop was upgraded from feisty on (purchased with feisty installed from dell):

```
$ cat /etc/issue
Ubuntu lucid (development branch) \n \l

``````

$ dpkg -l | grep grub
ii  grub                                              0.97-29ubuntu60                                  
GRand Unified Bootloader (Legacy version)
```


I have upgraded a dozen laptops, boxes, and servers to lucid and the only problem I experienced was a known bug with a broken flash installer package.

---

### Post by ranch hand on 2010-04-22
> **nanog said:**
> Upgrading does not convert grub legacy to grub. Upgrades are designed to be SAFE. 

```
$ cat /etc/issue
Ubuntu lucid (development branch) \n \l

``````

$ dpkg -l | grep grub
ii  grub                                              0.97-29ubuntu60                                  
GRand Unified Bootloader (Legacy version)
```
I really hate to point this out but about 85% of all the problems we are seeing right now about grub are on boxes that upgraded.

The problem is the method of switching from one to the other is badly flawed.  It is, not the other hand, quite easy to install grub2 before the upgrade.

This is a good idea.

Yes, you can stay with grub-legacy.  It is no longer supported.

---

### Post by nanog on 2010-04-22
"Yes, you can stay with grub-legacy.  It is no longer supported"

Grub-legacy is supported by ubuntu, redhat, novell, debian (and every major distro) for upgrades. The only reason to install grub2 is if you are switching file systems...and in that case you might as well reinstall. 

I personally plan on running ext3 on some of my boxes until they die.

---

### Post by ranch hand on 2010-04-22
> **nanog said:**
> "Yes, you can stay with grub-legacy.  It is no longer supported"

Grub-legacy is supported by ubuntu, redhat, novell, debian (and every major distro) for upgrades. The only reason to install grub2 is if you are switching file systems...and in that case you might as well reinstall. 

I personally plan on running ext3 on some of my boxes until they die.
Ah, that would be it then.

I have no trouble with grub-legacy, by the way, on ext4 in 9.04.  The Ubuntu devs did a fine job of making it compatible.

I do prefer clean installs but this install of 10.04 that I am on is a 9.04>9.10>10.04 upgrade and my oldest Lizard (10.04=Lounge Lizard) is a 9.10>10.04 on the first day the toolchain went up.

---

### Post by uRock on 2010-04-22
> **ranch hand said:**
> The package debfoster will create just such a list for you.

That's cool, I'll have to give it a try. The more I streamline those first few commands on an install, the faster and better an install will go.

---

### Post by recluce on 2010-04-22
> **ranch hand said:**
> Good plan.

A clean install will also avoid the problems with moving from grub-legacy to grub2.

If you, at some point, do decide you upgrade I would purge grub and grub common from 9.04.  Check to make sure all files are gone (particularly /boot/grub/menu.lst) and then install grub-pc and grub-common from the juanty repo (grub1.68).

The upgrade, other wise, leaves you with half one and half the other grub and it will eventually become unstable.  It has caused a lot of problems.  This is not the fault of either grub version.  It is just a stupid way of changing versions.

At least in theory this SHOULD not happen. If you upgrade an exisiting GRUB1 system, your system should remain GRUB1 all the way. If not, this would be a HUGE regression in a LTS release!

---

### Post by uRock on 2010-04-22
> **recluce said:**
> At least in theory this SHOULD not happen. If you upgrade an exisiting GRUB1 system, your system should remain GRUB1 all the way. If not, this would be a HUGE regression in a LTS release!

Regression? How? LTS just means it will get long term support. It doesn't mean that it will have support for legacy software.

---

### Post by recluce on 2010-04-22
> **nanog said:**
> "Yes, you can stay with grub-legacy.  It is no longer supported"

Grub-legacy is supported by ubuntu, redhat, novell, debian (and every major distro) for upgrades. The only reason to install grub2 is if you are switching file systems...and in that case you might as well reinstall. 

I personally plan on running ext3 on some of my boxes until they die.

Even if you switch to EXT4 on your root partition, you can stay with GRUB1, there is only one caveat: Ubuntu seems not to touch GRUB related binaries on Updates, EVER. In other words, if you originally installed Hardy, for example, you will still have Hardy's GRUB files. Just check the file dates. On such a system, you will see an error when trying to boot from EXT4. Workaround: copy the GRUB files from Jaunty, at the very least you need to replace "e2fs_stage1_5" and "stage2".

BTW: I am using GRUB1 (Jaunty version, dedicated GRUB partition) to boot Lucid (ext4), Jaunty (reiserFS), Windows XP, Windows 7 and PC BSD - no issues whatsoever.

---

### Post by ranch hand on 2010-04-22
> **recluce said:**
> At least in theory this SHOULD not happen. If you upgrade an exisiting GRUB1 system, your system should remain GRUB1 all the way. If not, this would be a HUGE regression in a LTS release!
You are given the choice.  The problem is that you really should be going to grub2.  That is where the problems come in.  I can not think of a better way to do it but the system is not very good.

I have upgraded 8.04.4 to 10.04 3 times with success.  On 2 of them I did not reboot before getting rid of grub-legacy and had no trouble.  Just purged, got rid of teh files and installed.  The other I rebooted and everything seemed fine for a couple weeks.

Then I installed another OS and that is when that one went down grub wise, as is the case with many of the grub problems on these forums today.  I then did a chroot purge job did the fresh install and it has been fine since then.

---

### Post by recluce on 2010-04-22
> **uRock said:**
> Regression? How? LTS just means it will get long term support. It doesn't mean that it will have support for legacy software.

Ubuntu DOES NOT change GRUB files on upgrades (edit: evidently, you are now given the choice. Just say no). If it would cause an upgrade from 8.04 to 10.04 have a half-cooked mix of GRUB1 and GRUB2, that would be a HUGE REGRESSION, as I said. Such an upgrade should leave an untouched GRUB1 system.

---

### Post by recluce on 2010-04-22
> **ranch hand said:**
> You are given the choice.  The problem is that you really should be going to grub2.


Why? I see no compelling reason at this time, especially during an upgrade. Even EXT4 support is easy to implement, if not supported anyway, see one of my earlier posts.

---

### Post by ranch hand on 2010-04-22
Ext4 support is in the newest version of grub0.97, as I pointed out in an earlier post.  I use it in one of my ext4 9.04 installs and it boots other ext4 OS' fine.

If you are on a one OS system, or even 2, grub-legacy is fine.  I am not on such a system.  There are 27 OS' currently on this box.  If you multi-boot, don't mind  learning new things and want the lowest possible time spent keeping your boot loader up to date, grub1.98 is just a whole lot easier to use.

---

### Post by recluce on 2010-04-22
> **ranch hand said:**
> Ext4 support is in the newest version of grub0.97, as I pointed out in an earlier post.  I use it in one of my ext4 9.04 installs and it boots other ext4 OS' fine.

If you are on a one OS system, or even 2, grub-legacy is fine.  I am not on such a system.  There are 27 OS' currently on this box.  If you multi-boot, don't mind  learning new things and want the lowest possible time spent keeping your boot loader up to date, grub1.98 is just a whole lot easier to use.

Isn't that more at matter of personal preference? I find it very easy to use GRUB1 on a dedicated GRUB partition and use that to chainload to other bootloaders (except for my main Ubuntu installation, which is booted directly). On a single OS or dual boot, I would probably tend to "never change a running system" and leave a boot-loader that is working well alone.

I have "only" five OS installed - how do you arrive at 27, unless you need many different configurations of the same OS for testing?

---

### Post by xebian on 2010-04-22
> **recluce said:**
> Ubuntu DOES NOT change GRUB files on upgrades (edit: evidently, you are now given the choice. Just say no). If it would cause an upgrade from 8.04 to 10.04 have a half-cooked mix of GRUB1 and GRUB2, that would be a HUGE REGRESSION, as I said. Such an upgrade should leave an untouched GRUB1 system.
An upgrade means to move up? So from grub1 to grub2 is proper.:confused:

---

### Post by ranch hand on 2010-04-22
> **recluce said:**
> Isn't that more at matter of personal preference? I find it very easy to use GRUB1 on a dedicated GRUB partition and use that to chainload to other bootloaders (except for my main Ubuntu installation, which is booted directly). On a single OS or dual boot, I would probably tend to "never change a running system" and leave a boot-loader that is working well alone.

I have "only" five OS installed - how do you arrive at 27, unless you need many different configurations of the same OS for testing?
I have 3 on my main internal drive, 6 on the other internal (3-32bit and 3-64bit) for demonstration.

I have 12 on my dual external enclosure for testing.  7 variations of 10.04, 9.04. Zenix 9.10, Mandriva2009-1 and 8.04.

I have the same mix as on my second internal an another external enclosure to lone to folks to try Ubuntu out on their hardware.

Yes, of coarse it is personal preference.

My wifes box has one OS, 9.10.  There are 2 entries on the menu.  That will not, and need not change as long as she is running a Debian based OS on the current / partition.

We can upgrade, get different kernels, change to a different flavor of 9.10, Lenny, PhatDebian, Mint, 9.04, what ever we want in that line and use the same 06_custom file on any of them with no editing at all.

I actually have always loved grub0.97.  Grub2 is easier to keep up and much more flexible.

---

### Post by recluce on 2010-04-22
> **xebian said:**
> An upgrade means to move up? So from grub1 to grub2 is proper.:confused:

Because people that upgrade (instead of doing fresh installs) usually just want a working system. So why exchange the boot loader? I would venture that 95% of users don't have an advantage from changing GRUB1 to GRUB2.

Also: what fault do you find with the statement "If it would cause an upgrade from 8.04 to 10.04 (to) have a half-cooked mix of GRUB1 and GRUB2, that would be a HUGE REGRESSION"? :confused:

And if I just want to "move up" without any good reason, I go climb a mountain... :P

---

### Post by nanog on 2010-04-22
ranch hand, if you have 27 oses you may want look into xen. its much easier to keep that kind of install organized on a bare metal system, imo.  you can even run oses simultaneously on a multicore box with almost no performance deficit.

---

### Post by RamR on 2010-04-22
Well, now I am confused again. :confused:

I think I will just do the clean install in a week.  Not sure about all the suggestions of things I should do before that though.

---

### Post by uRock on 2010-04-23
> **RamR said:**
> Well, now I am confused again. :confused:

I think I will just do the clean install in a week.  Not sure about all the suggestions of things I should do before that though.

This is what happens when folks start debating in help threads. Ranch Hand mentioned a nice program for finding which programs you have installed, which will help you get them installed and running quickly after your clean install.

If you are already using EXT4, then you need not worry about changing your partitioning. If you are running EXT3 you may want to upgrade the / partition to EXT4 to get the slightly faster speeds. No since messing with your /home unless you have everything backed up.

If you need any help be sure and let us know.

---

### Post by nanog on 2010-04-23
> Well, now I am confused again.you shouldn't be. upgrades are safe. the majority of people running lucid will have upgraded. a  minority of users (hobbyists and "testers") constantly reinstall.

> If you are running EXT3 you may want to upgrade the / partition to EXT4  to get the slightly faster speeds. 

first of all,  upgrading ext3 only gives you a theoretical increase in performance for new  extents.  your old files are kept as plain old journaled ext3.
[https://ext4.wiki.kernel.org/index.php/Ext4_Howto](https://ext4.wiki.kernel.org/index.php/Ext4_Howto)

secondly, ext4 is unfortunately quite as bit slower than ext3 on the 2.6.32 kernel as documented extensively at phoronix:

[http://www.phoronix.com/scan.php?page=article&item=linux_2632_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2632_fs&num=1)

---

### Post by uRock on 2010-04-23
> **nanog said:**
> you shouldn't be. upgrades are safe. the majority of people running lucid will have upgraded. a  minority of users (hobbyists and "testers") constantly reinstall.

 

first of all,  upgrading ext3 only gives you a theoretical increase in performance for new  extents.  your old files are kept as plain old journaled ext3.
[https://ext4.wiki.kernel.org/index.php/Ext4_Howto](https://ext4.wiki.kernel.org/index.php/Ext4_Howto)

secondly, ext4 is unfortunately quite as bit slower than ext3 on the 2.6.32 kernel as documented extensively at phoronix:

[http://www.phoronix.com/scan.php?page=article&item=linux_2632_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2632_fs&num=1)
And we wonder why people get confused. That site looks like it has been trying to debunk EXT4 since its inception into ubuntu. EXT4 has been faster on my machines. Lets keep the debating in the Cafe and out of the help threads.

---

### Post by nanog on 2010-04-23
[COLOR=Black]> That site looks like it has been trying to debunk EXT4 since its  inception into ubuntu.You are misinformed. Phoronix has been testing linux systems since 2004 and have an unvarnished reputation. This thread really needs to be closed.

> Lets keep the debating in the Cafe and out of the help threads.[/COLOR][COLOR=Black]
[/COLOR][COLOR=Black]I upgrade all of my systems. Repeatedly recommending that users not upgrade makes the forum less useful for users like me. Please stop.
[/COLOR][COLOR=Black]
[/COLOR]

---

### Post by uRock on 2010-04-23
> **nanog said:**
> [COLOR=Black]You are misinformed. Phoronix has been testing linux systems since 2004 and have an unvarnished reputation. This thread really needs to be closed.

[/COLOR][COLOR=Black]
[/COLOR][COLOR=Black]I upgrade all of my systems. Repeatedly recommending that users not upgrade makes the forum less useful for users like me. Please stop.
[/COLOR][COLOR=Black]
[/COLOR]

The OP's last post said he/she was confused. I don't mind if people go the upgrade route and I don't mind helping them when it fails, I prefer not to lead people through a route that is known to fail, especially when that route takes a person through running not one, but two upgrades, which doubles the risk of failure at the cost of hours waiting for the upgrade to complete.

Why would you want the thread closed when the OP may still need help? This is why we need to quit using people's help threads as debate zones. That's what blogs are for.

---

### Post by Longinus00 on 2010-04-23
> **uRock said:**
> The OP's last post said he/she was confused. I don't mind if people go the upgrade route and I don't mind helping them when it fails, I prefer not to lead people through a route that is known to fail, especially when that route takes a person through running not one, but two upgrades, which doubles the risk of failure at the cost of hours waiting for the upgrade to complete.

Why would you want the thread closed when the OP may still need help? This is why we need to quit using people's help threads as debate zones. That's what blogs are for.

The op is confused because people are just spouting off rhetoric rather than trying to help. The simple answer to the op's questions would have been
> You can upgrade from 9.04 to 10.04 by running distribution upgrade twice.

You can upgrade to RC but I would just wait for a week.

---

### Post by uRock on 2010-04-23
> **Longinus00 said:**
> The op is confused because people are just spouting off rhetoric rather than trying to help. The simple answer to the op's questions would have been

Not posting rhetoric. I ran 11 upgrades in the past year. All but one failed. At an average of 2 hours per upgrade, that is a loss of 20 hours not including the time spent running the clean install to fix them.

---

### Post by Longinus00 on 2010-04-23
> **uRock said:**
> Not posting rhetoric. I ran 11 upgrades in the past year. All but one failed. At an average of 2 hours per upgrade, that is a loss of 20 hours not including the time spent running the clean install to fix them.

I'll counter your anecdote with my own.

I can't remember ever having an ubuntu upgrade fail.

---

### Post by null_pointer_us on 2010-04-23
After a major release, the forums are usually filled with...
Upgrade to <codename> failed -- help!
...threads.

For myself, I would do a clean install, but there's no harm in trying to upgrade.

Personally, I cannot say enough good things about having a live CD. After confirming the live CD works, boot back into your 9.04 and do the upgrade (twice). Then, even if the worst happens and your 9.04 partition ends up unbootable, you can boot from the live CD to access your files, do backup/restore, etc.

---

### Post by cariboo on 2010-04-23
The reason most upgrades fail, from what I can see is that there are errors that the user ignores, and doesn't fix before rebooting. 

Usually running:

```
sudo apt-get -f install
```

then

```
sudo aptitude update && sudo aptitude safe-upgrade
```

will fix most of the problems.

---

### Post by RamR on 2010-04-23
When 9.10 came out I tried to upgrade to it and then I tried to do a clean install but there was something that caused the display not to work.  It soon became clear there was an issue.  As a result I stayed with 9.04.  Also as a result I would rather avoid the two step upgrade via 9.10.

The computer I am using this on is an old laptop with not too many files there and none that I would hate to lose.  Furthermore, there aren't many extra programs I need to keep track of.  So, this should be quite straight forward.

The thing that I'm questioning is the issue with the file system change.  If I do a clean install (which I'm leaning towards) do I need to change the file system beforehand?  Since my laptop is quite simple I think it would be do everything possible to set a solid foundation and it sounds like this might be one of those things.

---

### Post by Longinus00 on 2010-04-23
> **RamR said:**
> If I do a clean install (which I'm leaning towards) do I need to change the file system beforehand? 

No, you should be able to just reformat it in the installer. The only things that you might need to take into consideration should be covered by the release notes. [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

---

