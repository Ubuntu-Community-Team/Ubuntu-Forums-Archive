---
title: "Ubuntu FDE"
date: 2023-06-08
forum: Installation &amp; Upgrades
---

### Post by nevray on 2023-06-08
Here is an article on how to install Ubuntu on encrypted partitions, including /boot.
[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

Is it possible to do without lvm, and how to use luks2 for /boot? System is UEFI Secure Boot.
Here it says that luks2 pbkdf2 is supported for boot, but If I follow these instructions, the system won't boot.
[https://libreboot.org/docs/linux/encryption.md](https://libreboot.org/docs/linux/encryption.md)

What do I need to change in the article in the first link to make it all work?

---

### Post by TheFu on 2023-06-08
I don't know the answer to your question, but LVM is a gift, not a burden.  

Since you are willing to manually setup FDE (almost), then I'm guessing you have sufficient understand of all the great things that LVM provide.

For my effort, if I'm worried about the evil maid attack, I'll just bring a USB boot device with me and never let it leave my person. In these days of microSD cards, that's pretty easy.  I can appreciate when people want to be stubborn because something should work, but doesn't.  That isn't me when there is a practical alternative solution that doesn't cost anything or make me give money to companies I really, really, dislike.  YMMV.

For a long time, Ubuntu didn't support encrypted boot partitions.  I don't know if that has changed or not, since I stopped using laptops in early 2020.  When I start traveling again, I'll see what the defaults provide and probably end up with the microSD via USB adapter boot method again.

Regardless, the question is missing necessary information, like which release and which flavor.  There are some others here who have posted step-by-step guides for manually setting FDE.  Did you see those yet?

---

### Post by nevray on 2023-06-09
Separate small flash drive may be safe, but it is inconvenient. Lvm creates an extra layer of abstraction, which complicates the system, and I don't need its features. The release is the latest, I can choose any, I am reinstalling the system. 
> **TheFu said:**
> step-by-step guides for manually setting FDE
I would appreciate it if you could post links here to the guides you have encountered.

---

### Post by MAFoElffen on 2023-06-09
I have set up machines that are encrypted root and boot. With 20.04, you could encrypted the root to LUKS2, but had to encrypt the boot as LUKS1. With 22.04, you could encrypt both boot and root with LUKS2.

The differences there were the versions of Grub2. Grub2 couldn't read a LUKS2 volume until Grub2 version 2.06, which is the version 22.04 came with.

You told TheFu that 
> **nevray said:**
> 
Separate small flash drive may be safe, but it is inconvenient. Lvm  creates an extra layer of abstraction, which complicates the system, and  I don't need its features.

Wow.

Both could also be said about LUKS encryption. It is not "convenient', it does add another layer between things, and it does affect performance. It has it's place and purpose... Mostly targeted towards portable devices, where there is a concern about loss of physical security.

Ubuntu has a good install script that makes it easy and painless to do encrypted volumes with LVM. Yes, I heard your remarks. But you asked for input, and it was given freely. Your response to that was on the edge of just being rude, and displayed naivety.

Yes, you can use encrypted volumes on it's own, with LVM2, BTRFS, ZFS... Many variations and avenues to pursue. I just suggest that you whatever you do, do not use 'quiet' as a boot option... Remember that tip. It will save you from having to track down the LUKS prompt to unlock your volume(s).

I do all that from the command line, as prep to my installs. Before I start installing. I do type out a plan of how I want to lay things out, the commands I'll use... I come up with a recipe that I want to follow. 

Note-- I am the contributor to Yann, to the boot-repair and boot-info scripts for mounting ad rescuing LUKS encrypted systems and ZFS-on-root systems. So I have done some 'things' with those. (Understatement)

In a usual default install of encrypted volumes of root and boot, you will be asked twice for the phase-phrase, one for each volume... Unless you use a keyfile located by the cryptab... Usually on a USB Key being present during boot... Oh yes, you mentioned that USB's are "not convenient"... But truthfully, that "is" the accepted method for that, to make it easier, and more secure. The fall back for that is, if not present, to prompt for the passphrase... (or not)

I'm not sure what kind of help you might find after how you mistreated someone who was trying to help you and provide their advice and experience. He probably has more years of experience in high-level Systems Administrator, than you have been alive. Just saying. You might want to re-read, and think on that. Be courteous and open minded. That will get you much further.

---

### Post by nevray on 2023-06-09
> **MAFoElffen said:**
> I have set up machines that are encrypted root and boot.
Please explain in more detail how to do that all correctly from the  command line, or give me a link to an instructions where it is  described. Encrypted boot and root, using luks2 if it's better. It's a laptop, so  security is important. The guide in the very first link in this thread  uses a separate boot partition on the same drive where the system is  installed. If it's more secure to use the usb key, then I'll do it that  way. "The fall back for that is, if not present, to prompt for the  passphrase".

---

### Post by TheFu on 2023-06-09
> **nevray said:**
> Separate small flash drive may be safe, but it is inconvenient. Lvm creates an extra layer of abstraction, which complicates the system, and I don't need its features. The release is the latest, I can choose any, I am reinstalling the system. 

Not all versions of Ubuntu support booting in the same ways, so the version matters greatly. Some don't support booting from an encrypted /boot/ partition, for example. Plus the default Ubuntu LUKS encryption setup has a separate boot outside the LUKS container which holds the LVM PV, VG, and LVs for / and swap.  I usually reduce the / LV to be 35G, then create separate /var, /tmp, and /home LVs inside the VG.  I make them small, so there's room for snapshots and extending the SSD lifespan, then grow them only for what is needed over the next 3 months.

I see that MAFoElffen has joined us.  His knowledge in this area far, far, far, surpassed mine.  Interesting to see the different LUKS versions and how grub booting is tied into each.  Next time I load an OS onto a laptop, I'll try an encrypted /boot, but I'll still make a microSD to boot from when traveling to other countries.  For unlocking LUKS, I setup a few different Yubikeys with a challenge/response.  It is nice that LUKS has 8 slots that can be used for different decryption methods. I always have 1 that is 66+ characters, static, for emergency use by my lawyer. I doubt I could type that string into the computer myself, but it is part of my final documents so the family can gain access, which really isn't needed at all once I'm dead.

Encryption containers take up a full partition, typically.  If you don't want to have to enter a passphrase to access different partitions, then having a large single partition for the OS and data, while keeping personal data logically separate in different LVs is a gift.  The entire PV and VG would be inside 1 LUKS container, but there are somewhat important security reasons to have certain file areas mounted with different mount options, hence the need for separate LVs - say for /tmp/ and /var/ rather than allowing all those areas to be mounted with /.   Obviously, placing a file system onto each LV is another choice. Ubuntu prefers ext4 and LVM2 supports doing things with ext4 that are unsupported on any other file system.

Additionally, backups tend to be performed on a file system (though that isn't mandatory) level, so having specific data, settings and HOME directories in separate file systems (which would be separate LVs) makes sense, unless this is a toy system and just loaned out to people for a week or 2 at time when they travel internationally.

I know of no complete step-by-step guides with commands.  There is an expectation that someone wanting these things will read and understand the different topics and be able to convert that reading into the needed commands.  This sucks, I know.   Paddy may have made a step-by-step post in these forums.  You can search just as easily as I can.

Having a separate boot device on your person, means that if you and the laptop are separated, perhaps at a border crossing, then you can never trust the boot files on the laptop again.  With a USB boot drive (or microSD with a USB adapter), you'd know if that microSD was ever off your person, out of your control.  If it isn't, then you know it can be trusted.  I've had laptops taken at border crossings once. Fortunately, it was a fresh load of an OS with ZERO data and the people at that specific border didn't know Linux.  After that happened, I started traveling with a chromebook and used the guest account for everything, never connected any google account to the device.  
The border crossing issue (out of your control) comes up in every hotel too.  Leave a laptop on the desk in the room and an "evil maid" can bring in a small flash drive that analyzes then swaps out parts of the encrypted boot process, so your credentials to unlock the LUKS header are stolen.  Seems that a number of motherboard makers didn't really follow the secure boot standards, we've learned.  Even just 2 weeks ago, another vendor was caught violating Secure Boot standards.
Definitely best to boot from a microSD ... we can still have the main OS and data on LUKS encrypted storage inside the laptop.  LUKS does a good job with encryption.  A microSD can be carried with you everywhere and easily stored in a tiny waterproof baggie, though SanDisk says water doesn't impact their microSD storage.  Same for x-rays.  A tiny slot in a belt and that microSD would always be with you in the same room (showers).

Anyway, booting from the local device with any OS always has risks. I know some people who run their entire OS off USB flash storage and have done that for many years now.  Their laptop doesn't have any internal storage at all.  If it were me needing to do that, I'd have a small USB3.2 SSD connected for the OS, but that would be too hard to trust after going through a border. I'd still boot from a microSD.

BTW, I didn't see anything rude in the posts.  Just two people with different needs and opinions.  That's 100% expected and fine.  Perhaps I'm just dumb that way. Wouldn't be the first time.  The tone of posts often doesn't come through, so I try to assume the best from others. If I don't like what is said or the other party is asking for something I consider unreasonable, I'll stop posting if I don't know them from years of interactions here.  The long-time posters here all have a feel for each other's intentions - which is almost always to help.

---

### Post by MAFoElffen on 2023-06-09
> "I know of no complete step-by-step guides with commands. There is an expectation that someone wanting these things will read and understand the different topics and be able to convert that reading into the needed commands. "
Yes. There are a lot of bread crumbs here and there with invaluable pieces that we cobble together and make work.

As I remember TheFu uses one of my favorites in his security, a physical token: Yubikey HW token... And him talking about a removable boot drive...

That gave my an idea. I was thinking that it you used an encrypted /boot volume on a MicroSD card, and stored the key files on that drive, then you have built a physical token, that takes a few extra steps, in making the process more complex and harder to crack.

For Grub2 v2.06, so far it can only read LUKS2 /boot partitions, if it is using PBKDF2. But LUKS2 itself can use Argon2id. So (idea), set it up to ask the passphrase of the externally stored /boot partition with PBKDF2, so Grub2 can boot it... Then use LUKS2 with Argon2id, (with very long keys) for all the other pieces of your complex puzzle.

That way, without that physical token, it would be much more difficult to get around. But with it... One passphrase (It is possible to setup multiple passphrases for the same container.) Further, that one passphrase could be setup on a Yubikey or a card reader's access card to unlock the kingdom. But without that physical token, is harder to circumvent...

Why do I say "harder"? Because you can use dd to extract the LUKS header metadata from each LUKS container, and use that information to do a brute force attack to decrypt LUKS volumes and/or containers. I don't post the details online (but still can be found if you look). Keep the honest, honest. The thing to do for security is to make things harder and more complex. "Physical Security" is the primary factor there, as TheFu pointed out. Both of us worked in places that had 'security'. Where I worked, early on, you had security checkpoints, keypads, electronic locks, and safes/vaults, where the removable storage disks were removed and secured. Physical Security. After a while, that kind of thing makes for being a bit paranoid of the what-ifs, because you are made aware of those things. When I got out into the private secure, they were just not 'aware'.

But as TheFu preaches and is paramount, have good backups locked up somewhere.

EDIT: Appetizer for TheFu: [https://www.baeldung.com/linux/rsync-encrypted-remote-backups](https://www.baeldung.com/linux/rsync-encrypted-remote-backups)

---

### Post by nevray on 2023-07-14
The separate usb drive/Yubikey for boot is a very good idea and I'll probably do that.
> **TheFu said:**
> The entire PV and VG would be inside 1 LUKS container, but there are somewhat important security reasons to have certain file areas mounted with different mount options, hence the need for separate LVs - say for /tmp/ and /var/ rather than allowing all those areas to be mounted with /. 
Does this issue only occur when using LUKS or when installing the entire system (/) on a single physical partition without encryption (default installation) as well?

>>perhaps at a border crossing
As I know, unlike for example VeraCrypt, LUKS has a volume header with a signature, i.e. you can clearly establish the presence of such encrypted disks on the laptop. Can the password be forcibly demanded at the border, have there been such cases?

I am testing LUKS on a virtual machine with Ubuntu Cinnamon 22.04.2, Secure Boot. So far /boot on this test system is on the same physical disk, so as not to use a separate usb flash device.

This works:
[SIZE=1][SIZE=2]<PARTITION THE DISK MANUALLY (p1=efi, p2=boot, p3=root), then>[/SIZE]
export DEV_BOOT="/dev/nvme0n1p2"
export DEV_ROOT="/dev/nvme0n1p3"
export BOOT_CRYPT="boot_crypt"
export ROOT_CRYPT="root_crypt"
export VGNAME="vgubuntu"
cryptsetup luksFormat --type=luks1 ${DEV_BOOT}
cryptsetup luksFormat ${DEV_ROOT}
cryptsetup open ${DEV_BOOT} ${BOOT_CRYPT}
cryptsetup open ${DEV_ROOT} ${ROOT_CRYPT}
mkfs.ext4 /dev/mapper/${BOOT_CRYPT}
pvcreate /dev/mapper/${ROOT_CRYPT}
vgcreate "${VGNAME}" /dev/mapper/${ROOT_CRYPT}
lvcreate -l 100%FREE -n root "${VGNAME}"
while [ ! -d /target/etc/default/grub.d ]; do sleep 1; done; echo "GRUB_ENABLE_CRYPTODISK=y" > /target/etc/default/grub.d/local.cfg

[SIZE=2]<NOW RUN THE INSTALLER>[/SIZE]
partitions:
boot: ext4, format, /boot
vgubuntu-root: ext4, format, /

[SIZE=2]<AFTER INSTALLATION>[/SIZE]
mount /dev/mapper/${VGNAME}-root /target
for n in proc sys dev etc/resolv.conf; do mount --rbind /$n /target/$n; done
chroot /target
mount -a
apt install -y cryptsetup-initramfs
echo "KEYFILE_PATTERN=/etc/luks/*.keyfile" >> /etc/cryptsetup-initramfs/conf-hook
echo "UMASK=0077" >> /etc/initramfs-tools/initramfs.conf
mkdir /etc/luks
dd if=/dev/urandom of=/etc/luks/boot_os.keyfile bs=512 count=1
chmod u=rx,go-rwx /etc/luks
chmod u=r,go-rwx /etc/luks/boot_os.keyfile
cryptsetup luksAddKey ${DEV_BOOT} /etc/luks/boot_os.keyfile
cryptsetup luksAddKey ${DEV_ROOT} /etc/luks/boot_os.keyfile
echo "${BOOT_CRYPT} UUID=$(blkid -s UUID -o value ${DEV_BOOT}) /etc/luks/boot_os.keyfile luks,discard" >> /etc/crypttab
echo "${ROOT_CRYPT} UUID=$(blkid -s UUID -o value ${DEV_ROOT}) /etc/luks/boot_os.keyfile luks,discard" >> /etc/crypttab
update-initramfs -u -k all
<REBOOT>[/SIZE]

Now trying to switch /boot to LUKS2 PBKDF2, so instead of
[SIZE=1]cryptsetup luksFormat --type=luks1 ${DEV_BOOT}
[/SIZE]I use
[SIZE=1]cryptsetup luksFormat  --type luks2 --pbkdf pbkdf2 ${DEV_BOOT}[/SIZE]

As a result, after rebooting I get this:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292468&stc=1[/IMG]
Where's the error, why isn't it working?

---

### Post by TheFu on 2023-07-14
> **nevray said:**
> The separate usb drive/Yubikey for boot is a very good idea and I'll probably do that.

Don't have just 1 method to unlock LUKS.  There are 8 slots, use 3.  As soon as you only have one, that's when you'll lose the yubikey and be locked out forever.  I have 2 yubikeys setup for challenge/response and 1 really long, random, passphrase that I doubt I could type correctly even with it in front of me.  Remember, at boot time, we have to type. No select/paste.

> **nevray said:**
> 
Does this issue only occur when using LUKS or when installing the entire system (/) on a single physical partition without encryption (default installation) as well?

They are part of the default install for nearly all Linux distros, encrypted or not.

> **nevray said:**
> 
>>perhaps at a border crossing
As I know, unlike for example VeraCrypt, LUKS has a volume header with a signature, i.e. you can clearly establish the presence of such encrypted disks on the laptop. Can the password be forcibly demanded at the border, have there been such cases?


The border matters, since every country has different laws.  Also, your ability to deal with the "real-world hassle" factor would drastically change for most people. Some countries won't let you enter without providing them access to your social media accounts.  If you refuse, you are sequestered overnight and put on a flight home.  

Other countries don't recognize any rights to withhold any encryption from them. A few are European.  So, when crossing a border there and either refusing or claiming you cannot unlock encryption of a device, I don't know what will happen. I'm not an EU citizen.

Upon returning to my home country, the rules for what immigration can and cannot search have been fluid.  I believe in May, a court ruled that border searches of phones and computers needs a warrant, which requires probable cause to get [https://www.theregister.com/2023/05/31/us_border_phone_search/](https://www.theregister.com/2023/05/31/us_border_phone_search/)  I think that's the correct ruling. Criminals who have used electronics to get information/plans through borders shouldn't get a free pass, but visitors who have no history or belief to be doing anything nefarious shouldn't be hassled either.  Smart people wouldn't bring huge amounts of encrypted storage across borders anyway.  It takes next to nothing to leave it at home and access it from almost anywhere in the world securely today.

If they do have a warrant when I return and demand access, now I get to decide how I'd like to handle it. If they don't have any proof of actual wrong doing, they can't prevent me from entering the country. They can hold me for 3 days, but it is more likely they will hold me a few hours, if I refuse.  Just long enough to create a hassle for any connections. They can also keep the device(s) in question.  I travel with devices I expect to have lost or stolen, so that's not really an issue for me.  Eventually, those devices must be returned after a "reasonable" period.  6-12 months has been deemed reasonable here, so plan accordingly.

These days when traveling, it is probably easier to have a microSD with the OS and files on it for the OS you will really be using and have just a fresh install on the internal storage.  Your choice.

> **nevray said:**
> 
I am testing LUKS on a virtual machine with Ubuntu Cinnamon 22.04.2, Secure Boot. So far /boot on this test system is on the same physical disk, so as not to use a separate usb flash device.
22.04 is too new for my needs.

> **nevray said:**
> 

...

Stuff I don't do/use.

> **nevray said:**
> 
As a result, after rebooting I get this:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292468&stc=1[/IMG]
Where's the error, why isn't it working?
TBD .... I don't see any attachment.

---

### Post by nevray on 2023-07-17
> **TheFu said:**
> Don't have just 1 method to unlock LUKS
Yeah, that's a good idea.
> They are part of the default install for nearly all Linux distros, encrypted or not
So any linux installation with default settings on a single partition will be insecure? What would be better to put on separate partitions (necessary minimum)? /var, /tmp, /home ? or /home doesn't need to? Should swap be moved to a separate partition or left as a file? On systems that do not use encryption, do I need to put /boot on a separate partition for security reasons?

Reloaded the attachment

---

### Post by TheFu on 2023-07-17
> **nevray said:**
>  
So any linux installation with default settings on a single partition will be insecure? What would be better to put on separate partitions (necessary minimum)? /var, /tmp, /home ? or /home doesn't need to? Should swap be moved to a separate partition or left as a file? On systems that do not use encryption, do I need to put /boot on a separate partition for security reasons?
 

Security is about mitigating risks.  All computers have risks.  Security experts mitigate all that are easy and some that are hard, if they are likely to happen.  Only you can decide whether any specific risk is likely and worth mitigation or not.

There are many hardening guides. Some are more hassle than 99% of people are willing to deal with.  Only you can answer that question.

And honestly, I don't know all the security risks for any specific setting. That's impossible.  If a computer is powered on, there is risk.  If a computer is networked, there is risk.  If a computer allows physical access, there is risk.  If any USB port is enabled, there are huge risks.  Most people trade convenience for increased risk.  I do as well.  If I want to store data and not have the risks of networking, I'd use a computer that doesn't have any network capability.  I have a PalmPro like that. The interface to it is serial, only. But it also can't store much data, which is inconvenient.

Mount options are a common way to reduce risks for specific sensitive areas.  Having all mounts using the same options as the / file system uses would be a risk. Some people choose to mitigate it, but there is a convenience factor that most people, including the people who setup the stock installation layouts, consider.

---

### Post by nevray on 2023-07-24
Why replacing the
```
[SIZE=2]cryptsetup luksFormat --type=luks1 ${DEV_BOOT}[/SIZE]
```with
```
[SIZE=2]cryptsetup luksFormat  --type luks2 --pbkdf pbkdf2 ${DEV_BOOT}[/SIZE]
```doesn't work? Why do I get to grub instead of normal boot after rebooting?
How to understand why it doesn't work? What commands should I use for troubleshooting?

---

