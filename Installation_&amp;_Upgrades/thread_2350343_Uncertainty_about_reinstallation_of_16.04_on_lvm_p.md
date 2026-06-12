---
title: "Uncertainty about reinstallation of 16.04 on lvm partition"
date: 2017-01-23
forum: Installation &amp; Upgrades
---

### Post by matthew-bluteau on 2017-01-23
Having posted two related questions on the Ask!Ubuntu stack exchange now with no responses, I have found my way over to the Ubuntu forms hoping there might be a bit more capability for assistance here. I would classify myself as a somewhat experienced user: comfortable with command-line and tinkering with configurations, but lacking in a deep under-lying knowledge of many aspects related to OSes/computers in general. Most of the content of this message is reproduced from the two mentioned questions which can be found at the following links:

[https://askubuntu.com/questions/873792/failure-of-release-upgrade-from-14-04-lts-to-16-04-lts-because-of-ubuntu-desktop](https://askubuntu.com/questions/873792/failure-of-release-upgrade-from-14-04-lts-to-16-04-lts-because-of-ubuntu-desktop)
[https://askubuntu.com/questions/875288/uncertainty-about-reinstallation-of-16-04-on-lvm-partition](https://askubuntu.com/questions/875288/uncertainty-about-reinstallation-of-16-04-on-lvm-partition)

As explained in the first link, I attempted an upgrade from 14.04 LTS to 16.04 LTS, and everything went smoothly until just near the end when I got a message that although the upgrade had been installed, some errors had occurred. Doing a bit of digging, it seemed that the 'ubuntu-desktop' package had some unsolvable dependencies. Please see first link above for relevant outputs from /var/log/dist-upgrade/apt.log and my attempts to resolve dependencies with aptitude (I don't want to clog this question with too much output). My system has been a little buggy ever since. This led me to the likely conclusion that the issue was due to a conflict between qtbase-abi-5-5-1 and qtbase-abi-5-6-1 as pointed out in posts #12 and #14 at [https://answers.launchpad.net/ubuntu/+question/433070](https://answers.launchpad.net/ubuntu/+question/433070) . 

The suggested solutions from the launchpad post are:

[LIST=1]
[*]a complete new installation of xenial (to go back to qtbase-abi-5-5-1)
[*]an upgrade to xakkety (everything there should be based on qtbase-abi-5-6-1) *==> I don't like this option because I want LTS*
[*]eventually a manual installation of selected packages from yakkety ==> *sounds patchy*
[*]leave the system as it is (without unity-tweak-tool) ==> *not really an option since I have already installed whatever packages are causing the problems and mine was not related to unity-tweak-tool*
[/LIST]

I have opted for a new installation of Xenial, unless anyone here can tell if I have misinterpreted. Before settling on clean install, I wanted to see if re-installation was a possibility (i.e. keep /home and configs), hence the second question from above: [https://askubuntu.com/questions/875288/uncertainty-about-reinstallation-of-16-04-on-lvm-partition](https://askubuntu.com/questions/875288/uncertainty-about-reinstallation-of-16-04-on-lvm-partition) . I have backed up /home by various means (some of it is through my own Seafile sync, some through a git repository, and the remainder via Deja-Dup), so a clean install is certainly possible but feels like it might be more of a hassle: I have never really gone through the process of restoring /home or other configurations. I have also backed up my list of software sources and installed packages which I plan to prune following (re-)installation. I am aware that this request somewhat puts me in the category of "[COLOR=Red]**Well, I get your point, but I have installed so many applications on my system that a clean install is basically out of the question**.[/COLOR]" from the sticky in this subforum, but I am mostly double checking I am not doing a clean install unnecessarily. I have also tried the recommended last ditch efforts of rebuiliding my source list (but I think ppas are still included, should I disable these?) and the series of apt-get commands.

Questions related to re-installation:

[LIST=1]
[*]The LiveUSB I am using for installation does not recognise that there is already an operating system on the hard drive. Should I be worried by this, and does it not bode well for my prospects of re-installation? I have also tried using a LiveCD with exactly the same results.
[*]The link above makes no mention about what happens if you installed with an lvm2 partition, which is what I did (perhaps foolishly because I know nothing about it). The link simply says to select the 'Ubuntu system partition', but I don't really know what this would be in my case: see two thumbnails below
[*]If I was to select the second entry (/dev/mapper/ubuntu--vg-root) as the root of the file system to be installed (which is my suspicion at the moment), I am unsure what to select as the device for the boot loader installation: would it be /dev/sda or /dev/mapper/ubuntu--vg-root?
[/LIST]

[ATTACH=CONFIG]273348[/ATTACH][ATTACH=CONFIG]273349[/ATTACH]

I can appreciate this is quite the burgeoning, extended question, so partial answers and suggestions are more than welcome. Anything that gets me towards a solution!

Some selected system information:
```
 
$ sudo lshw
# pruned
    vendor: LENOVO
    version: ThinkPad W540
    width: 64 bits
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
     *-memory
          description: System Memory
          size: 16GiB
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 41
          version: GNET66WW (2.14 )
          date: 07/02/2014
          size: 128KiB
          capacity: 11MiB

$ uname -a
Linux matthew-ThinkPad-W540 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

$ lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial






```

---

### Post by DuckHook on 2017-01-24
Welcome to the forums, matthew-bluteau

> **matthew-bluteau said:**
> Having posted two related questions on the Ask!Ubuntu stack exchange now with no responses, I have found my way over to the Ubuntu forms hoping there might be a bit more capability for assistance here.
Yes, UF tends to be a bit more conversational.

You appear to have a complex installation. If I might summarize:

[list=1]
[*]You installed on a logical volume
[*]You have added PPAs
[*]You did not disable those PPAs and revert/purge their components before upgrading
[*]You now have an incomplete upgrade/install
[*]You now have stubborn, inconsistent, "buggy" behaviour
[*]You have tried a number of "fixes" that have further complicated the situation
[/list]
In view of all the above, you > …have opted for a new installation of Xenial, unless anyone here can tell if I have misinterpreted
In your case, I think this is a wise choice.
> I wanted to see if re-installation was a possibility (i.e. keep /home and configs)
This is relatively easily done even if you don't have a separate /home partition, but I'm not sure if you would want it&#8213;for reasons to follow later. For now, it is enough to point out that backfilling a fresh /home directory with all of your old /home data from a backup achieves the results you are taking about.
>  I have backed up /home…through my own Seafile sync…a git repository…Deja-Dup)
This does not constitute a real backup. You will want a complete, single, tested and demonstrably restorable backup before doing a new install.

Now onto the larger issues:

Only an educated guess on my part, but your old install has likely been so customized that the network upgrade failed because it could not sort things out. The existence of qtbase-abi-5-6-1 is one indicator of this. It is not part of either a default Trusty or Xenial install. The likeliest reason it was in your old system was because a PPA dragged it in there. Since you then tried to upgrade without purging your PPAs, which *might*&#8213;not even *would*&#8213;have reverted your libraries to their defaults, apt could not figure things out and threw in the towel. Result: incomplete (read "failed") upgrade.

This is the same reason that you should beware of simply backfilling your old /home directory. Since it is more than probable that your old install is full of wonky customized components, do you really want to drag back all of your old config files? If the purpose of a fresh install is to purge your OS of irregularities&#8213;a fresh restart, as it were&#8213;why would you, as your first action, want to polute that new install with the unknown configs that led to your current predicament?

Since you:> …plan to prune following (re-)installation……anyways, then refrain from resurrecting the unknowns and unknowables that may be the root of your problems. Granted it's a chore, but it's not really that hard to reconfigure the settings that you want in a new install.

Your backed up data can then also be carefully pruned&#8213;bringing back only the pure data: photos, music, video, docs, email, browser bookmarks, etc and leaving behind all the cruft. With a proper backup, say, on an external USB HDD, it is easy to restore at any later time data that you might subsequently find needful.

A new install will also give you the opportunity to get rid of the LVM. While there is nothing inherently bad about using LVMs (a few of my installs are done on them) they add unnecessary complexity unless you really need them. They are usually only needed if you must use whole-disk encryption. Otherwise, they are the purview of tinkerers and mad-gurus.

In your case, I would recommend the following:

[LIST=1]
[*]Make a proper, robust, simple and demonstrably restorable backup of all your important data. I would not bother with deja dup. Use rsync, because every file is an exact reproduction and therefore readable from any Linux machine.
[*]Using a LiveUSB, fire up gparted and completely nuke your old system HDD/SSD. No LVM, no bells, no whistles, no pixie dust.
[*]Install a simple, pristine, standard OS that is absolutely default.
[*]At first boot, do *NOT* reinstall your PPAs. Don't make the same mistake twice.
[*]Instead, install a VM. Your machine is a powerful little beast. It will handle multiple VMs easily.
[*]Within these VMs make further installs of Ubuntu.
[*]Then install your PPAs *inside of these sandboxed, revertable and disposable VMs.*
[*]But always, always keep your host OS stupidly simple. Satisfy your experimental hankerings using VMs instead.
[/LIST]
I have answered your "burgeoning, extended question" with a burgeoning, extended answer. But it contains many years of experience, most of which was learned the hard way. The most obvious principle in my recommended strategy is the KISS principle. If you practice it, it will save you from this grief on your next upgrade.

Let us know how it goes.

---

### Post by matthew-bluteau on 2017-01-24
Thank you for the thorough reply DuckHook! It is nice to know one isn't shouting into the abyss, and it's comforting to get a more expert opinion.

> **DuckHook said:**
> 
Yes, UF tends to be a bit more conversational.

It sounds like I have found the right place then :)

This is a great, concise summary of my situation that I completely agree with:
> 
 You appear to have a complex installation. If I might summarize:

[LIST=1]
[*]You installed on a logical volume
[*]You have added PPAs
[*]You did not disable those PPAs and revert/purge their components before upgrading
[*]You now have an incomplete upgrade/install
[*]You now have stubborn, inconsistent, "buggy" behaviour
[*]You have tried a number of "fixes" that have further complicated the situation
[/LIST]

Having done a lot of reading in the past few days, the disabling of PPAs and subsequent purging should have been something I did before upgrading, along with a host of other items. I didn't really do any prep before the upgrade and simply dove into clicking the gui "Update Now" button that had been pestering me for however many months 16.04.1 has been available. Obviously, this was inadvisable, but one can only gain experience by having experiences. However, this dodges the larger issue of keeping a simple host OS that you mention.

Overall, I think you have convinced me of the rationale for restoring only "pure data" to /home: not wanting to "pollute" a fresh install with the unknown problems from a previous install is as good a reason as any. My hesitancy about doing so and ditching configurations mostly arose from my inexperience and desire for a quick fix. 


A few follow up questions/comments on your advised course of action.
> 
1. Make a proper, robust, simple and demonstrably restorable backup of all your important data. I would not bother with deja dup. Use rsync, because every file is an exact reproduction and therefore readable from any Linux machine.

I will need to invest in a new external USB HDD for this, so trying out all that follows may be a bit delayed. Having an offline backup is something I have always known I should do, but never got around to it. I have a large one attached to a raspberry pi that I use for my Seafile file syncing server mentioned in my first post and always contented myself that at least I was doing something.
> 
2. Using a LiveUSB, fire up gparted and completely nuke your old system HDD/SSD. No LVM, no bells, no whistles, no pixie dust.

Can this also be achieved by selecting the "Erase disk and install Ubuntu" option in the installation program? Or is wiping the HDD/SSD with gparted beforehand advisable? If so, could you provide or point me towards a few specifics of the best way to "nuke" a HDD with gparted?
> 
3. Install a simple, pristine, standard OS that is absolutely default.

4. At first boot, do *NOT* reinstall your PPAs. Don't make the same mistake twice.

When transferring my "pure" data over at this point from the backup, what should be done with git working copies? Should I re-clone or transfer the entirety of the working copy and any git dotfiles from the backup? 
> 
5. Instead, install a VM. Your machine is a powerful little beast. It will handle multiple VMs easily.

6. Within these VMs make further installs of Ubuntu.

7. Then install your PPAs *inside of these sandboxed, revertable and disposable VMs.*

8. But always, always keep your host OS stupidly simple. Satisfy your experimental hankerings using VMs instead.

This makes a lot of sense. Any recommendations/guides for setting up VMs? I have experience with Oracle's VirtrualBox. One of my crucial apps from a PPA is Zotero (reference manager), and it would need access to my database of PDF journal articles on my host machine, so there would need to be shared folders between the host and guest OSes: I don't have any experience doing that. Alternatively, I think I can install Zotero from source, but this avoids that fact that I am going to want to have "integrated" VMs that don't impinge on my workflow: or does this defeat the principle of *sandboxing*?


Thank you again for your reply. I will keep this thread updated as I progress.

---

### Post by DuckHook on 2017-01-25
> **matthew-bluteau said:**
> …Can this also be achieved by selecting the "Erase disk and install Ubuntu" option in the installation program?
Yes, you can repartition during the installation process using the partition manager that is part of Ubiquity. It is just a pretty pseudo-GUI front end for *parted*.
> Or is wiping the HDD/SSD with gparted beforehand advisable?
I mentioned this only because most people find *gparted* more friendly and easier to understand and use. But it also is just a pretty GUI for *parted*. I like it because it gives me a chance to ponder what my partitions should look like in advance, without the pressure of a running install process hovering over my head.
> If so, could you provide or point me towards a few specifics of the best way to "nuke" a HDD with gparted?
Nuking a HDD is couldn't be simpler&#8213;you just delete the old partition table and create a new one in its place. Once you "apply" those changes, there is no going back. All of your old partitions along with the data therein should be considered dead and gone. This will apply to your LVM too. Getting rid of partitions is never the challenge. It's the design and layout of the new ones that demand some planning and thought.

It seems to me that your data needs are sufficiently complex that you would be better off with a separate data partition. This is where you would put all of the data that you want to survive upgrades and reinstalls. Once the new install is in place, simply symlink the data back to their expected locations and you will have a running system with relatively little pain.
> When transferring my "pure" data over at this point from the backup, what should be done with git working copies? Should I re-clone or transfer the entirety of the working copy and any git dotfiles from the backup?
It's been years since I cloned a git repo and I only did it once that time. My suggestions may be out to lunch regarding these and are not based on expertise. However, I don't see why you can't restore your old data and directories to your new data partition and create symlinks in your VM OSes where git expects to find them. However, you are best advised to seek the advice of more knowledgeable forum members on that one.
> Any recommendations/guides for setting up VMs? I have experience with Oracle's VirtrualBox.
VBox is also what I use (for now). I find it easy and simple. The VBox website is very useful for setting up this app. If you decide to add this PPA into your host OS, you can make it one of the few exceptions to the rule.
VBox user manual is: [https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)
The Ubuntu VBox website is: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
> …there would need to be shared folders between the host and guest OSes
VBox has a very handy feature that allows you to create a *Public* folder that is shared between the host and the guest. This involves *guest extensions* which is covered in VBox's website. Every VM you create can share this same folder. If you go the additional step of storing this folder on your data partition (and creating a symlink to it in your /home directory), then this data will also survive upgrades and reinstalls.
> …I can install Zotero from source
You shouldn't assume that installing something from source won't mess with your dependencies. If an app needs newer libraries, then it will either install them or ask you to install them, else it just won't run, irrespective of whether it is installed from source or a PPA. The best way to deal with this is using VBox.
> …I am going to want to have "integrated" VMs that don't impinge on my workflow: or does this defeat the principle of *sandboxing*?
Anything that accesses your disk or network outside of the VM itself&#8213;such as the aforementioned *Public* directory&#8213;by definition is a penetration of the sandbox and increases your exposure footprint. However, the idea of sandboxing is really a red herring in your case because you are not using VMs for reasons of security. Rather, you want them because you want to segregate your PPAs from your host system. Since this is the driving motive, penetrating the sandbox is not really a big deal. Besides, if you develop a need for a fully sandboxed VM, then simply create one without a *Public* directory and you've closed off that hole.

If you have further questions beyond this point, I encourage you to ask them as separate queries, split down to only one on each pertinent subforum. While these wall-of-text exchanges can be useful, they don't attract the quality responses that you will find the most useful and concise.

---

### Post by matthew-bluteau on 2017-01-25
Thank you again for the exemplary and helpful replies! I have a clear path towards solving my situation, and so I will mark this thread as solved. I will pose any derivative questions in separate threads to cease our "wall of text" exchanges :razz: and engage with some other members of the forum.

Cheers!

---

### Post by DuckHook on 2017-01-25
Glad to have helped. I'm sure we will run into each other again on the forums.

Good Luck and Happy Ubuntu-ing!

---

