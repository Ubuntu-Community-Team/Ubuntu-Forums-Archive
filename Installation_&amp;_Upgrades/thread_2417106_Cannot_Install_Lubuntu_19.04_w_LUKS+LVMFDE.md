---
title: "Cannot Install Lubuntu 19.04 w/ LUKS+LVM/FDE"
date: 2019-04-20
forum: Installation &amp; Upgrades
---

### Post by thatrandomguy+ on 2019-04-20
Hello,

I'm up to my ends with this as I've tried nearly everything possible via the installer and I can only come to the conclusion that it's impossible.

I'm trying to setup a FDE install where I have separate home and root partitions using LUKS/LVM.

Lubuntu has decided to switch over to the **Calamares** installer, so I've gone under the assumption that any work-arounds that required **Ubiquity** will not work.

_What I've tried so far_:
1) Provision LVM, run Calamares, and attempted to setup distinct partitions with encryption enabled (LUKS) from installer.
2) Provision LUKS container, setup basic LVM, run Calamares and created typical/distinct partitions via installer.
[ATTACH=CONFIG]283072[/ATTACH]

Both attempts fail for obvious reasons and reasons I'm still not too sure about exactly. Calamares failed in the first attempt while the second attempt didn't even go through the partition creation because it "couldn't".
[ATTACH=CONFIG]283073[/ATTACH]

In both cases, Calamares obviously recognized my provisions correctly and allowed me to create my desired partitions under the scheme I wanted, but it always fails for whatever reason when it comes time to commit these configs.

I would be more than happy to go into further detail with what steps I took, but after what I've been through, am I correct in assuming the only way to get this working would be to essentially have the one root partition encrypted?

From the failed attempts, I get the feeling that's the only way to get FDE. My particular target setup involves a UEFI machine which I can set to legacy BIOS. So far, I haven't tried doing that and have tried getting the UEFI route to work.

Am I correct in my assumptions? Will this only work with one non-LVM partition under LUKS?

Additional Info on attempt 2:
[ATTACH=CONFIG]283074[/ATTACH][ATTACH=CONFIG]283075[/ATTACH]

---

### Post by TheFu on 2019-04-20
Setup the normal, single partition install with LVM+LUKS.
Then come back and reduce the size of the the root-lv to make room for your home-lv.  Create the home-lv, mount it to a temp location and move all the files over, then mount it to /home/.  Easy, peasey.

```
$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                         8:0    0 465.8G  0 disk
&#9500;&#9472;sda2                      8:2    0   732M  0 part  /boot
&#9500;&#9472;sda1                      8:1    0   512M  0 part  /boot/efi
&#9492;&#9472;sda3                      8:3    0 464.6G  0 part
&#9474; &#9492;&#9472;sda3_crypt            253:0    0 464.6G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root     253:1    0    25G  0 lvm   /
&#9474;   &#9500;&#9472;ubuntu--vg-home--lv 253:3    0    75G  0 lvm   /home
&#9474;   &#9500;&#9472;ubuntu--vg-stuff    253:4    0   100G  0 lvm   /stuff
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1   253:2    0   4.5G  0 lvm   [SWAP]
```

I didn't test this on anything newer than 16.04, but it works there, as shown above.  I had enough room left for /stuff to hold things I don't need to ever have backed up. Any they are all encrypted. Nice.

In my install the default size of the swap was much too small, under 1G, so after a few terrible slowdowns, I rememberd that 4.1G is the correct answer for swap for any desktop and did that.  I need to reduce it a tiny bit next chance I get.

Gotta love LVM.  I don't remember doing any of this outside the running OS since it wasn't touching any partitions.  Rock on with your LVM!

---

### Post by thatrandomguy+ on 2019-04-21
@TheFu

I don't think that works with 19.04. Considering they (Lubuntu & Ubuntu) use different installers, I don't know of any guide that makes use of my desired setup with Calamares. I did see posts and tutorials for getting FDE with Ubiquity, however.

I added a screenshot for what I see when attempting to create a setup using LVM+LUKS where LVM is provisionally created within a LUKS container (which I create *before* running the installer).

Incidentally, after reading your post, I recalled some fuss being made over LUKS2 not being supported by GRUB; so I repeated the procedure with a LUKS1 container and I received the same outcome.

I can't tell if it's something I'm doing wrong or if it's just a limitation with the installer, Calamares.

I tried to reach out to the Lubuntu folk but IRC blocks me every time I use my VPN. Since they don't have a forum, I felt the next best thing was to come here.

---

### Post by Dennis N on 2019-04-21
> Since they don't have a forum, I felt the next best thing was to come here.
Lubuntu has a mailing list. You can join and ask your question, or just browse the archives and learn. I think the maintainers participate here.
[https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users)

---

### Post by dino99 on 2019-04-21
You seems to be the most skilled guy around such settings  with calamares (found many of your own posts/questions).
In case there is something usefull to discover:
[https://github.com/calamares/calamares](https://github.com/calamares/calamares)
and possibly  open a bug/request  to get some devs comments.

---

### Post by TheFu on 2019-04-21
> **thatrandomguy+ said:**
> @TheFu

I don't think that works with 19.04. Considering they (Lubuntu & Ubuntu) use different installers, I don't know of any guide that makes use of my desired setup with Calamares. I did see posts and tutorials for getting FDE with Ubiquity, however.

I added a screenshot for what I see when attempting to create a setup using LVM+LUKS where LVM is provisionally created within a LUKS container (which I create *before* running the installer).

Incidentally, after reading your post, I recalled some fuss being made over LUKS2 not being supported by GRUB; so I repeated the procedure with a LUKS1 container and I received the same outcome.

I can't tell if it's something I'm doing wrong or if it's just a limitation with the installer, Calamares.

I tried to reach out to the Lubuntu folk but IRC blocks me every time I use my VPN. Since they don't have a forum, I felt the next best thing was to come here.

The setup I showed above is current, after I did all the changes via LVM, manually.
Are you saying that the Wipe everything, use LVM+FDE in the Lubuntu installer doesn't work at all? 

Or am I misunderstanding?

I generally don't touch non-LTS releases due to the extremely short support periods.

---

### Post by thatrandomguy+ on 2019-04-22
> **TheFu said:**
> The setup I showed above is current, after I did all the changes via LVM, manually.
Are you saying that the Wipe everything, use LVM+FDE in the Lubuntu installer doesn't work at all?

I actually don't recall trying that. I will post my results on that later today. Thanks for the reminder. :)

---

### Post by thatrandomguy+ on 2019-04-22
Update:

I tried the wipe option but that seemed to only provision the standard partition type and did not involve LVM in any way. Better said, there's no option for LUKS+LVM within the installer itself.
[ATTACH=CONFIG]283085[/ATTACH][ATTACH=CONFIG]283086[/ATTACH][ATTACH=CONFIG]283087[/ATTACH]

I signed up to the appropriate mailing list and hope to get some support on this soon.

I'm just going to conclude it's impossible for now on **Lubuntu** 19.04. It looks possible on 16.04 and 18.04 but I'm assuming that's largely due to the installer they have.

Oh well. :-\"

I'll just settle with having / encrypted with LUKS and then later setting up ecryptfs on home/swap. No biggie.

---

### Post by TheFu on 2019-04-22
Or install 'server'  which does support LUKS+LVM and add the lxde-desktop metapackage.  Did all Ubuntu flavors change to the same installer and remove LVM+LUKs?  I know there was a push for mainstream Ubuntu to get ZFS to be the OS partition, but they couldn't finish is up before the release.

ecryptfs was deprecated for a few reasons. Be certain those reasons are understood.
 
I've always much preferred the customization of storage in the CentOS distro.  Basically, we have control of everything there and don't have to fight to setup storage how we want.  Ubuntu has dumbed it down so much as to be too stupid.

---

### Post by thatrandomguy+ on 2019-04-23
> **TheFu said:**
> Did all Ubuntu flavors change to the same installer and remove LVM+LUKs?
I think Lubuntu are the only ones to use something other than Ubiquity (flavor-wise). The installer technically supports LUKS/LVM... it just doesn't support all use-cases.
> ecryptfs was deprecated for a few reasons. Be certain those reasons are understood.
 :wink:
> I've always much preferred the customization of storage in the CentOS distro.  Basically, we have control of everything there and don't have to fight to setup storage how we want.  Ubuntu has dumbed it down so much as to be too stupid.
I didn't think about that before but that does ring a bell. Also, I *very much* agree with the last sentiment. I was installing Ubuntu on a relative's desktop recently and noticed the installer has gone through some weird changes since I last used it.

---

