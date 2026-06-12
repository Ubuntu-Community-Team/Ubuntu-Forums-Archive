---
title: "Partitioning /home/ separately from multiple distros"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by Ashocka on 2011-09-16
Hi,

I currently have Ubuntu 10.4 but I am wanting to do what many others do and put their /home/ directory on a separate partition so they can install some other distros but configure them so that they all mount the same /home/ directory.

Would appreciate any tuts, pros, cons contributions or pointing to good articles on how to do this the best way.

Thanks
Geoff

---

### Post by ~!geek!~ on 2011-09-16
> **Ashocka said:**
> Hi,

I currently have Ubuntu 10.4 but I am wanting to do what many others do and put their /home/ directory on a separate partition so they can install some other distros but configure them so that they all mount the same /home/ directory.

Would appreciate any tuts, pros, cons contributions or pointing to good articles on how to do this the best way.

Thanks
Geoff

Its cool to put /home on a separate partition. It helps a lot in situations when you need to reinstall the operating system (Happens a lot after distro upgrade in ubuntu!!!). 
But its not advisable to share same user directory with a number of distros! Its my personal opinion because I don't want some distro to screw with my settings which I would loved on ubuntu otherwise!
I would suggest, you select same /home for each distro but create different users for each of them. Each of them will  have their configurations in different directories this way in same /home partition! You may copy basic configurations for each of them like: .mozilla directory, .thunderbird etc. for each of them or create symlinks for them to point to a common directory! Also I would suggest you put the heavy directories such as Documents, Downloads, videos etc. on some storage partition and create symlinks to those for each user! I hope I am making sense!!
To have separate /home for each distro is easy once you create one /home for one distro. For others you just [B]choose this /home partition and please make sure format option is not active while choosing it. If its selected you will lose your precious data.
[/B]I m not able to provide links for you but you could just google with query : create separate /home partition linux or other combinations!!!

---

### Post by Ashocka on 2011-09-16
> **~!geek!~ said:**
> Its cool to put /home on a separate partition. It helps a lot in situations when you need to reinstall the operating system (Happens a lot after distro upgrade in ubuntu!!!). 
But its not advisable to share same user directory with a number of distros! Its my personal opinion because I don't want some distro to screw with my settings which I would loved on ubuntu otherwise!
You know, I was thinking this exactly, so I am **really** glad you said this
> 
I would suggest, you select same /home for each distro but create different users for each of them. Each of them will  have their configurations in different directories this way in same /home partition! You may copy basic configurations for each of them like: .mozilla directory, .thunderbird etc. for each of them or create symlinks for them to point to a common directory! Also I would suggest you put the heavy directories such as Documents, Downloads, videos etc. on some storage partition and create symlinks to those for each user! I hope I am making sense!!
You are making heaps of sense. Thanks
> 
To have separate /home for each distro is easy once you create one /home for one distro. For others you just **choose this /home partition and please make sure format option is not active while choosing it. If its selected you will lose your precious data.**
Okay thanks, I'll watch out for that gotcha
> 
I m not able to provide links for you but you could just google with query : create separate /home partition linux or other combinations!!!
That's probably enough to get me searching for the right stuff, thanks, now that I know what strategy to implement because of this info.  The great thing is that there is so much information out there to find solutions, it just helps a lot when someone can point you in the right direction strategically.

Thanks

---

### Post by Ashocka on 2011-09-16
> **~!geek!~ said:**
> For others you just [B]choose this /home partition and please make sure format option is not active while choosing it. If its selected you will lose your precious data.

This is where giving meaningful labels to partitions really helps deter such mistakes.

I also like being able to keep a daily backup of such partitions to save from such mistakes.

---

### Post by srs5694 on 2011-09-16
FWIW, I do it the same way that ~!geek!~ suggests, although I typically use the same username but different home directories. (This is possible, but Ubuntu doesn't make it easy to set it up this way when you first install. Some other distributions offer more advanced options that make this easier.)

Some other people advocate using a separate partition for user data to be shared across distributions. This works, too, and it's a more obvious solution if you're coming from a Microsoft perspective; but from a Unix/Linux perspective it's re-inventing the wheel.

One other word of advice: In my experience, it gets to be very tedious to maintain more than a couple of Linux distributions on a single computer. In the past year or two, I've taken to using [VirtualBox](http://www.virtualbox.org) to install different distributions in virtual machines. This simplifies maintenance, particularly of boot loaders and partitions, and it becomes much easier and safer to wipe an installation and try again. Depending on your needs, you might want to look into VirtualBox or other virtualization tools (VMware, QEMU, etc.) rather than dual booting. If you're just curious about another distribution, virtualization is a good way to "get your feet wet," as it were. Likewise if you just need it for occasional access. If you think you might want to switch your primary distribution, then you might consider using the other distribution in a virtual environment for a while and then, if you like it, install it in a dual boot configuration. If you end up using it more, you'll then have the option of reclaiming your original distribution's disk space if/when you get tired of maintaining it.

---

### Post by Ashocka on 2011-09-16
> **srs5694 said:**
> FWIW, I do it the same way that ~!geek!~ suggests, although I typically use the same username but different home directories. (This is possible, but Ubuntu doesn't make it easy to set it up this way when you first install. Some other distributions offer more advanced options that make this easier.)

Some other people advocate using a separate partition for user data to be shared across distributions. This works, too, and it's a more obvious solution if you're coming from a Microsoft perspective; but from a Unix/Linux perspective it's re-inventing the wheel.
Thanks, but can you say more about why from a Unix/Linux perspective it's re-inventing the wheel?
> 
One other word of advice: In my experience, it gets to be very tedious to maintain more than a couple of Linux distributions on a single computer. In the past year or two, I've taken to using [VirtualBox](http://www.virtualbox.org) to install different distributions in virtual machines. This simplifies maintenance, particularly of boot loaders and partitions, and it becomes much easier and safer to wipe an installation and try again. Depending on your needs, you might want to look into VirtualBox or other virtualization tools (VMware, QEMU, etc.) rather than dual booting. If you're just curious about another distribution, virtualization is a good way to "get your feet wet," as it were. Likewise if you just need it for occasional access. If you think you might want to switch your primary distribution, then you might consider using the other distribution in a virtual environment for a while and then, if you like it, install it in a dual boot configuration. If you end up using it more, you'll then have the option of reclaiming your original distribution's disk space if/when you get tired of maintaining it.
Yes, have used VB before (mainly for Windows), but I had problems getting full HD screen resolutions.  But I have a new graphics card now so I should go back and take a look at it.  It's much more practical approach to this solutions for trying out distros, but can you get a similar config for /home for all distros under VB?  Also, I'm under the impression that connecting with external devices under VB isn't always as easy???

So what am I trying to do?  Long time ago I was a RH user, then Debian, which was much better until I had to install Java (back in those days it was a problem... not now.)

Past few years I have been mainly using Ubuntu and LinuxMint.  But now I want a KDE environment for development.  Probably will use aptosid as Mepis doesn't like my current machine (which is unusual for Mepis).

The other thing is just keeping pace with user friendly Linux distros to recommend to Windows users and low end machine users.  My local LUG, a bunch of retired geeks, mainly go with Salix (They are long time Slackware/Suse/Mepis/Debian based users), and I also want to have a look at Arch.

So from what you say I'd probably best install aptosid onto the HDD and maybe the others in VB?

(Thanks for the post, it has contributed to the thread)

---

### Post by srs5694 on 2011-09-16
> **Ashocka said:**
> Thanks, but can you say more about why from a Unix/Linux perspective it's re-inventing the wheel?

Using a separate /home partition uses the home directory structure in the way it was intended (as described in the [Filesystem Hierarchy Standard, or FHS](http://www.pathname.com/fhs/pub/fhs-2.3.html)). Using a separate non-/home data partition isolates most user data on a separate partition (just as does a separate /home partition), but with a couple of differences: Some user data (mostly configuration files, but perhaps some other files, depending on how you use it) will end up on the same partition as the OS; and the data partition will necessarily go in some non-standard location, thus placing user data in an odd location. Neither of these issues is really bad enough to be called a "problem," but they do make the solution less like a typical Unix/Linux solution than using a separate /home partition with unique subdirectories of that for each installation.

> Yes, have used VB before (mainly for Windows), but I had problems getting full HD screen resolutions.  But I have a new graphics card now so I should go back and take a look at it.

That might be a limitation of the emulated video card in VirtualBox. Personally, I run my emulated systems in windows (rather than full-screen) using whatever resolution seems appropriate, so I've not dealt much with trying to match my monitor's resolution. What is your native resolution? I recall that there are differences between BIOS mode and UEFI mode in what resolutions are supported, so you might have better luck using one mode or the other.

> It's much more practical approach to this solutions for trying out distros, but can you get a similar config for /home for all distros under VB?

With the right configuration, yes. You'd need to set up an NFS server on the host machine and export /home. (Alternatively, a Samba server would work, but it would be less clean for a Linux-to-Linux share.) You'd then mount the exported /home directory on the virtual machines, at which point you can use them in much the same way you'd use a shared /home partition on a multi-boot configuration.

> Also, I'm under the impression that connecting with external devices under VB isn't always as easy???

That depends on the device and the version of VirtualBox. I've done very little with this myself, though.

Depending on the device, a network option might work. For instance, you could configure an NFS server to give VirtualBox access to the /media directory, which should give you access to USB flash drives and external disks. (I've not tried this myself, though; I'm just speculating about what *should* work, given my understanding of the system.)

> Past few years I have been mainly using Ubuntu and LinuxMint.  But now I want a KDE environment for development.  Probably will use aptosid as Mepis doesn't like my current machine (which is unusual for Mepis).

If all you want is KDE, you can install it along with whatever else you like on Ubuntu and switch between them by logging out, selecting a different disktop environment, and logging back in. There are also ways to create logins in a window or by running multiple instances of X (so you can switch by using Ctrl+Alt+F*n*, much as you can switch to text mode from X).

> The other thing is just keeping pace with user friendly Linux distros to recommend to Windows users and low end machine users.  My local LUG, a bunch of retired geeks, mainly go with Salix (They are long time Slackware/Suse/Mepis/Debian based users), and I also want to have a look at Arch.

For this, you'd need multiple computers, a multi-boot setup, or a virtual environment. My preference for just keeping up to date would be a virtual environment, which is easier and safer to manage than the other options.

One more point: There are virtualization tools other than VirtualBox. I used to use QEMU a lot, and it's got its advantages, particularly for emulating non-x86/x86-64 systems; but it's slow and awkward compared to VirtualBox for emulating x86 or x86-64 systems on an x86-64 machine. VMware has a lot of fans, but it's commercial, so I haven't dealt with it in years. My impression is that Xen gives better low-level access to hardware for guests, but I've never gotten very far in getting it set up.

---

### Post by garvinrick4 on 2011-09-16
Hope I am not restating:
If you use the same /home between a debian and a Redhat or cousins (fedora and such)
Ubuntu uses a UID of 1000 and Redhat (or yums) use a UID of 500 so the permissions will
get out of sync. If you change permissions in yum's to fit that distro in /home then
it makes the wrong permissions in ubuntu so be wary of using same /home between
different distro's. This is in my experience's with /home between different distro's.
Look into before doing anyway. Some good users on the subject in these forums can
make a thread if want to try.

---

### Post by srs5694 on 2011-09-16
> **garvinrick4 said:**
> Hope I am not restating:
If you use the same /home between a debian and a Redhat or cousins (fedora and such)
Ubuntu uses a UID of 1000 and Redhat (or yums) use a UID of 500 so the permissions will
get out of sync. If you change permissions in yum's to fit that distro in /home then
it makes the wrong permissions in ubuntu so be wary of using same /home between
different distro's. This is in my experience's with /home between different distro's.
Look into before doing anyway. Some good users on the subject in these forums can
make a thread if want to try.

Different user ID (UID) values for a single user poses no problems whatsoever for sharing a single /home partition. Different UID values *will* create problems when sharing a *user home directory* (/home/fred, /home/jane, or whatever), but as has been specified earlier, that's a bad idea anyhow. Different UID values will sometimes make it difficult or impossible to read and write files (including directories) created in one distribution in another one, no matter whether you share a /home partition, share a non-/home data partition, or store user files in a /home directory on the root (/) partition and then access those root (/) partitions across distributions.

The solution is generally to synchronize your UID values across distributions. This can be done after installation by using the text-mode usermod command in one distribution or the other. (You'd do something like "usermod -u 1000 fred" to change the user fred's UID to 1000. If files are stored outside of the user's home directory, they'll need to have their UIDs adjusted separately -- that's one of the little ways in which sticking to the usual Unix/Linux conventions, rather than using a separate data partition, can be beneficial, since usermod should change the UID of files in the user's home directory.) It's probably better to do this in Fedora rather than in Ubuntu, since 1000 is a perfectly reasonable UID in Fedora, whereas 500 is below the normal lowest UID (for ordinary users) of 1000 in Ubuntu. You can also run usermod in Fedora in a direct root login, which is less likely to cause glitches than running it with sudo to modify your own regular account in Ubuntu.

---

### Post by Ashocka on 2011-09-24
> **srs5694 said:**
> What is your native resolution?
1,920×1,080
> 
With the right configuration, yes. You'd need to set up an NFS server on the host machine and export /home.
Thanks for that, I'll read up on that.
> 
If all you want is KDE, you can install it along with whatever else you like on Ubuntu and switch between them by logging out, selecting a different disktop environment.
I am looking for a fresh install as one of the problems I encounter is with custom pointing devices running under Ubuntu.  Because I am 56yo, with a chronic neck problem limiting my perception, I need to run customised pointing devices and resolutions (large fonts), So I'm looking to find a distro which doesn't freak out when I customise and tweak these.
> 
For this, you'd need multiple computers, a multi-boot setup, or a virtual environment. My preference for just keeping up to date would be a virtual environment, which is easier and safer to manage than the other options.
Yes
Thanks

---

### Post by Ashocka on 2011-09-24
> **garvinrick4 said:**
> Hope I am not restating:
If you use the same /home between a debian and a Redhat or cousins (fedora and such)
Ubuntu uses a UID of 1000 and Redhat (or yums) use a UID of 500 so the permissions will
get out of sync. If you change permissions in yum's to fit that distro in /home then
it makes the wrong permissions in ubuntu so be wary of using same /home between
different distro's. This is in my experience's with /home between different distro's.
Look into before doing anyway. Some good users on the subject in these forums can
make a thread if want to try.
Thanks for pointing that out

---

### Post by Ashocka on 2011-09-24
> **garvinrick4 said:**
> Hope I am not restating:
If you use the same /home between a debian and a Redhat or cousins (fedora and such)
Ubuntu uses a UID of 1000 and Redhat (or yums) use a UID of 500 so the permissions will
get out of sync. If you change permissions in yum's to fit that distro in /home then
it makes the wrong permissions in ubuntu so be wary of using same /home between
different distro's. This is in my experience's with /home between different distro's.
Look into before doing anyway. Some good users on the subject in these forums can
make a thread if want to try.

Thanks for point that out

---

### Post by srs5694 on 2011-09-24
> **Ashocka said:**
> [quote=srs5694]What is your native resolution?1,920×1,080[/QUOTE]

That seems to be higher than VirtualBox supports in EFI mode, as per [this page.](http://www.virtualbox.org/manual/ch03.html#efi) (See the description of "VBoxManage setextradata".)

---

### Post by Ashocka on 2011-09-24
> **srs5694 said:**
> That seems to be higher than VirtualBox supports in EFI mode, as per [this page.](http://www.virtualbox.org/manual/ch03.html#efi) (See the description of "VBoxManage setextradata".)
Okay, thanks for pointing that out.

---

