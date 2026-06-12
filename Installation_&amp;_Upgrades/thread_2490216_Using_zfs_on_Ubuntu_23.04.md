---
title: "Using zfs on Ubuntu 23.04"
date: 2023-08-26
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2023-08-26
I am setting up a new computer and drives. 

 zfs can be installed by 

```
sudo apt install zfs

```
I have not use it because I want to be sure how to set up  zfs on 23.04? 

Here is an article on ubuntu and zfs but it does not cover the way to get all the drives running zfs:

> 
[https://www.howtogeek.com/272220/how-to-install-and-use-zfs-on-ubuntu-and-why-youd-want-to/](https://www.howtogeek.com/272220/how-to-install-and-use-zfs-on-ubuntu-and-why-youd-want-to/)

Using the installer:

When installing a new setup, via manual partitioning,  if you click a partition, choose change,  the drive being set up can be changed from Ext4 to  zfs root. The term "zfs root" implies it is only for the root partition. Is that correct?

Looking under the option to do an  "advanced"  install,  only LVM is offered.

---

### Post by Dennis N on 2023-08-26
> Looking under the option to do an "advanced" install, only LVM is offered. 
If you are using the new "Ubuntu Desktop Installer" that is available for 23.04, then the ZFS option for installing isn't available. You can read that here:
[https://www.phoronix.com/news/Ubuntu-23.04-No-OpenZFS](https://www.phoronix.com/news/Ubuntu-23.04-No-OpenZFS)

Also, the new installer does not support all cases for installing LVM, such as installing to an existing LV. The only thing you can do with LVM is use the erase disk option with it.

An alternate ISO of 23.04 has the old Ubiquity installer, which may work.

---

### Post by Robbyx on 2023-08-27
> If you are using the new "Ubuntu Desktop Installer" that is available for 23.04, then the ZFS option for installing isn't available. You can read that here:
[https://www.phoronix.com/news/Ubuntu-23.04-No-OpenZFS](https://www.phoronix.com/news/Ubuntu-23.04-No-OpenZFS)

I have looked at the phoronix ref and it covers a lot of problems. Thank you.

Using  the new installer there  is still an option  to format a partition to  zfs_root. Does this mean that the new installer can format drives  to zfs, but there after, zfs has to be manually installed and setup through command line instructions?

---

### Post by MAFoElffen on 2023-08-27
That is outdated news.

Subuitity was fixed for the ZFS canned installer script in the package ubiquity - 22.04.19, on 2.08.2023. 

This is from my test VM from that installer:
```

mikeferreira@mikeferreira-Standard-PC-Q35-ICH9-2009:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              309M  1.20G       96K  /boot
bpool/BOOT                                         308M  1.20G       96K  none
bpool/BOOT/ubuntu_0ir34z                           308M  1.20G      308M  /boot
rpool                                             6.46G  17.3G       96K  /
rpool/ROOT                                        6.45G  17.3G       96K  none
rpool/ROOT/ubuntu_0ir34z                          6.45G  17.3G     4.62G  /
rpool/ROOT/ubuntu_0ir34z/srv                        96K  17.3G       96K  /srv
rpool/ROOT/ubuntu_0ir34z/usr                       224K  17.3G       96K  /usr
rpool/ROOT/ubuntu_0ir34z/usr/local                 128K  17.3G      128K  /usr/local
rpool/ROOT/ubuntu_0ir34z/var                      1.83G  17.3G       96K  /var
rpool/ROOT/ubuntu_0ir34z/var/games                  96K  17.3G       96K  /var/games
rpool/ROOT/ubuntu_0ir34z/var/lib                  1.83G  17.3G     1.70G  /var/lib
rpool/ROOT/ubuntu_0ir34z/var/lib/AccountsService    96K  17.3G       96K  /var/lib/AccountsService
rpool/ROOT/ubuntu_0ir34z/var/lib/NetworkManager    136K  17.3G      136K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_0ir34z/var/lib/apt              96.1M  17.3G     96.1M  /var/lib/apt
rpool/ROOT/ubuntu_0ir34z/var/lib/dpkg             35.7M  17.3G     35.7M  /var/lib/dpkg
rpool/ROOT/ubuntu_0ir34z/var/log                  2.23M  17.3G     2.23M  /var/log
rpool/ROOT/ubuntu_0ir34z/var/mail                   96K  17.3G       96K  /var/mail
rpool/ROOT/ubuntu_0ir34z/var/snap                 1.52M  17.3G     1.52M  /var/snap
rpool/ROOT/ubuntu_0ir34z/var/spool                 112K  17.3G      112K  /var/spool
rpool/ROOT/ubuntu_0ir34z/var/www                    96K  17.3G       96K  /var/www
rpool/USERDATA                                    6.33M  17.3G       96K  /
rpool/USERDATA/mikeferreira_5rqqmw                6.12M  17.3G     6.12M  /home/mikeferreira
rpool/USERDATA/root_5rqqmw                         120K  17.3G      120K  /root

```
That was from the installer > Type Erase Disk and install ZFS...

What does not work still with that installer is what the OP tried to do. It is an invalid option in that partitioner, that will never work. I have a bug still filed against that. The OP tried to go to other, and format a partion as "ZFS". That is invalid there, because that is just how ZFS works.

I could go into much detail on that, but in the end, that option is not possible from there.

Robin-- 1fallen and I explained and referred you to the OpenZFS documents, where it goes into detail how to do that manually. In that process, you can see that ZFS is much like BTRFS and LVM2. It's a file manager, where you create nested containers within each other, which are then mounted into the filesystem. ZFS just happens to have it's own filesystem, much like BTRFS, which when you create a pool, formats that container with it's own filesystem. Then you create dataset containers within those pools. That is more complex of what I needed to say about that, but you can see that the process of that is not just a format option.

---

### Post by Dennis N on 2023-08-27
> Does this mean that the new installer can format drives to zfs, but there after, zfs has to be manually installed and setup through command line instructions?
I'm only aware of the limitations of the new installer. I don't use ZFS myself, so can't say if there is a workaround for installing it. There are some ZFS users on this forum. One of them may give you an answer as to how installing might be done.

---

### Post by MAFoElffen on 2023-08-27
I am one of those Users... We must have been posting at the same time. LOL.

---

### Post by Robbyx on 2023-08-27
Thank you both for your helpful comments and explanations. I understand now much more. 

Robin

---

### Post by #&amp;thj^% on 2023-08-27
Robin MAFoElffen and I had also mentioned to first try it iin a KVM just to get a feel for it.
And with your current down-loaded .iso not showing an option for the ZFS-Root there is a work around.
Boot to the Live installer and *before* you do the install you may need to run this:
```
sudo apt  update

sudo apt install zfsutils-linux zfs-initramfs zfs-zed
```
Now when you launch the Live Installer the ZFS option should now appear in the Advanced Section of the installer.
It works on KVM install as well.

---

### Post by MAFoElffen on 2023-08-27
@1fallen--

After work last nigh (almost 2am), I downloaded the 23.04 installer last night (twice) and installed ZFS (once). It no longer needed the work-around to work. I believe **if** you download it **now**, they have that fixed also.

I tested the "traditional" installer last night...

I did notice it had two flavors of installers on the download page: The installer and the traditional installer. I didn't get a chance at 2 in the morning to test the (new/regular) installer last night. I'll test that again 'now'...

Will make a new post with that test...

---

### Post by #&amp;thj^% on 2023-08-27
> **MAFoElffen said:**
> @1fallen--

After work last nigh (almost 2am), I downloaded the 23.04 installer last night (twice) and installed ZFS (once). It no longer needed the work-around to work. I believe **if** you download it **now**, they have that fixed also.

I did notice it had two flavors of installers on the download page: The installer and the traditional installer, I didn't get a chance at 2 in the morning to test the traditional installer last night. I'll test that again 'now'...

I thought so from our last help request months back, I'm just curious why Robin did not have that option, or perhaps did not know where to find it???
I have heard but not laid my hands on the new installer yet. Correct me if I'm wrong but the Flutter installer was only for Ubuntu/Gnome is that correct?

---

### Post by MAFoElffen on 2023-08-27
The new installer did not offer to install ZFS, but had the new partitioner that if you start it via "Manual Partitioning", has that invalid option to format as ZFS...

So download and install via the Lunar 23.04 "Traditional" Installer image: [https://cdimage.ubuntu.com/releases/lunar/release/ubuntu-23.04-desktop-legacy-amd64.iso?_ga=2.184038374.19569560.1693127188-339163398.1632768351](https://cdimage.ubuntu.com/releases/lunar/release/ubuntu-23.04-desktop-legacy-amd64.iso?_ga=2.184038374.19569560.1693127188-339163398.1632768351)

@1fallen -- Sent you some PM's

---

### Post by #&amp;thj^% on 2023-08-27
> **MAFoElffen said:**
> 
@1fallen -- Sent you some PM's
Got them Thanks, and thanks for the looks at both installers.
Yippy a new problem to triage>>>>>>LOL
Flutter: [https://ubuntu.com/blog/how-we-designed-the-new-ubuntu-desktop-installer](https://ubuntu.com/blog/how-we-designed-the-new-ubuntu-desktop-installer)

---

