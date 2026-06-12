---
title: "Jaunty x64 + dmraid + nvidia: Experiences, problems"
date: 2009-02-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by silanea on 2009-02-13
Hallo!

I'd like to both share my experiences so far with installing Jaunty and ask for advice or at least raise awareness on some issues I found. First off, before you slap me with file-a-bug replies: I **will** file bug reports once I have sorted out my installation and done proper research on already filed ones. This post is meant as a way to verify whether I am really experiencing bugs or whether I just messed up my system. Plus it should give others with similar systems and setups advice on what to watch out for.

**Hardware**
[LIST]
[*]CPU: AMD Phenom 9850 Black Edition (4x2.5 GHz)
[*]Mainboard: ASUS M3N-HT deluxe (BIOS rev. 0901)
[*]RAM: 2x GeIL Black Dragon EVO ONE PC2-8500U 2GB
[*]Video cards: 2x Gainward GeForce 8800 GT 1GB
[*]Hard-disks: 2x Seagate Barracuda ES.2 500GB
[*]Optical drive: LG - some S-ATA DVD recorder
[/LIST]

**Pre-existing installation**
[LIST]
[*]The two drives are configured as a striping RAID array in the on-board controller.
[*]Two primary partitions exist on the set, both NTFS, that contain a Windows 2008 installation and combined consume about half of the set's space.
[*]The rest of the set's space was left empty.
[/LIST]

**Used Jaunty version, preconsiderations**
[LIST]
[*]I downloaded [FONT="Courier New"]jaunty-desktop-amd64.iso[/FONT] on Feb. 11 and used UNetBootin 3.12 to put the installer on a Microdrive plugged into a USB card reader.
[*]I wanted to keep my Windows installation untouched and use the rest of the set's space up.
[*]I specifically wanted to try out Jaunty and Ext4. Since I keep all my personal data on my server and don't rely on this Ubuntu installation for productivity (at least not for now) I don't mind having to reinstall Ubuntu should the file system - or Jaunty itself - change or prove to be unusable.
[*]I had read about the issues lots of people have with getting NVIDIA's proprietary video drivers to run. After reading in a bug discussion that the current version should run relatively fine I decided to try them out. They were no requirement though, just a nice-to-have.
[/LIST]

**Intended partitioning**
[LIST]
[*]Primary 1: Windows (leave untouched)
[*]Primary 2: Windows (leave untouched)
[*]Primary 3: /boot (Ext2, ~200MB)
[*]Logical 4: swap (8GB)
[*]Logical 5: / (Ext4, all the rest)
[/LIST]

**The installation - Basics**
[LIST]
[*]I booted into the live system. First things I did was enabling all software sources (to get my beloved joe) and run all updates on the live system.
[*]Since my raid set requires dmraid, I installed that from the repos. Got me version 1.0.0.rc15andthensome. No matter what I did I could not get the set to activate. No useful error messages, no nothing. It just didn't do anything. Yahoo brought the answer: RC 15 is somehow broken, the previous RC should be fine. I downloaded dmraid and libdmraid packages from FTP (specifically [FONT="Courier New"]dmraid_1.0.0.rc14-2ubuntu12.1_amd64.deb[/FONT] and [FONT="Courier New"]libdmraid1.0.0.rc14_1.0.0.rc14-2ubuntu12.1_amd64.deb[/FONT]), installed them manually via ```
sudo dpkg -i {first the lib's file name, then the app's file name}.deb
```, ran ```
sudo dmraid -ay
``` and voilà - the set was activated.
[/LIST]

**The installation - Partitioning**
Partitioning turned out to be a real b***h:
[LIST]
[*]First I tried to just run the setup from desktop. I chose manual partitioning, created all the partitions as laid out above - and the setup failed after creating the filesystems. I didn't write down the exact message, but as far as I can remember it complained about no root file system being there. I fired up GPartEd to see what the setup had done. The partitions were created as expected, though the Ext4 one was shown as unknown type. I decided to scrap them and set them up myself only to find out that GPartEd does not support Ext4.
[*]partman to the rescue. Or so I thought. After Idunnohowmany attempts I finally got the partitions set up.
[*]I started setup again, chose manual partitioning, set the mount points and boot flags on my newly created partitions - and received a message about no root point (or something along those lines) being defined. No way to go anywhere.
[*]I tried several ways to set up the partitions, I tried deleting them and letting setup partition the disk - one of these options worked for me. I don't remember exactly which one, but I believe the automatic setup plus a little handiwork in partman did the trick. The installation went through without any further issues.
[/LIST]

**The installation - Getting dmraid into the new installation**
I mounted the base partition, then mounted the boot partition and the live system's dev and proc into it, chrooted into it, and then the fun began:
[LIST]
[*]First I edited /etc/apt/sources.list and enabled all sources, then updated the system.
[*]Installing the dmraid packages I downloaded earlier was painless. I forgot to mark them as locked so they would not get updated to the non-functional RC15, I did that later from the installed system's desktop.
[*]Setting up grub turned into nightmare:
[LIST]
[*]I managed to configure it using the UUIDs from the live system and install it onto the raid set. Or so I thought. The first reboot gave me a "file not found" grub error. Great.
[*]Back into the live system, dmraid set up again, chroot set up again. Fixed the menu.lst, (just to be safe) regenerated the initramfs, rebooted. Ended up in a busybox complaining about no file system to boot from.
[*]Back into the live system and chroot. Added the dmraid kernel module to /etc/initramfs/allow (or something along those lines, anyways the file where you put modules you want included into your initramfs image) and regenerated the image. Rebooted, again a busybox.
[*]Now I started poking around: The dmraid module was there and loaded, but apparently did not activate my raid set. I ran ```
dmraid -ay
``` and voilà: The set and its partitions appeared in /dev/mapper.
[*]I entered ```
exit
``` and the system booted to the login screen. Woohoo! That problem still persists, though (see end of post), so whenever I say "Reboot, do thisandthat" from now on, insert "run dmraid -ay;exit" in between.
[/LIST]
[/LIST]

**The installation - nvidia drivers**
[LIST]
[*]First I tried the one-click driver installation from within the desktop. I chose the newer driver (180, I think; the other one was 177 or something). Installation finished, X restarted - and came up with a much lower resolution that could not be changed. The Display tool from Gnome complained that a different setup tool should be used, NVIDIA's setup tool complained that no NVIDIA drivers were loaded. Nice.
[*]I decided to go back to the default (open) driver and start from there again. Since I didn't find an option to do that from that one-click tool (the 180 driver was declared as installed, but not activated, and could not be brought to life) I threw any packages that started with nvidia from the system via Synaptic. Removed /etc/X11/xorg.conf, restarted X - and back to where it was right after boot. I then searched the web for info, found some posts suggesting the official NVIDIA downloads, other posts flaming those posts and instead recommending the Ubuntu packages, and decided to take another look in Synaptic. I installed two packages - the latest NVIDIA driver, don't remember the package name, and some nvidia configuration package -, ran ```
nvidia-xconfig
```, rebooted the machine - and was rewarded with a login screen at my display's native resolution, and compiz eye-candy once logged in. I considered myself blessed, began to adapt the system to my liking and finally shut it down.
[*]Upon the next boot I did not get a friendly Gnome login; instead I saw a shell login and the screen flickered about 3 times, about 1 second apart. Then nothing, just the shell. Logged in, typed ```
startx
``` and received an error message about "No screen found".
[*]I checked all logs, I checked the xorg.conf - no idea what the hell happened. xorg.conf did contain a screen, and any other parts that I would have expected to be there. I ran ```
sudo nvidia-xconfig
startx
``` again, same result. I deleted the xorg.conf, tried to start X, another error. Ran dpkg-reconfigure on X, no solution. Short of purging and reinstalling the whole X shebang I have no idea what to do. The very config that worked perfectly fine before the last shutdown now produces an illogical error. ](*,)
[/LIST]

**Remaining issues**
[LIST]
[*]I want my NVIDIA back! I would be fine without it if it had never worked. But since I know that it can run on my machine, I want it to work. It's aggravating, really. Well, I'll go back to messing with X once I find the time.
[*]I have not even the faintest clue what dmraid is up to in the busybox. It clearly is loaded, and once I run it manually it activates the raid set just fine. But it should do that on its own. Since I don't really have much knowledge of the Linux boot process at that stage I'll skim the forums and delve into whatever resources Yahoo may bring me to find out what the hell is going on here.
[/LIST]
If you could help with one of those issues, please please please do so! Any help is greatly appreciated.

I will update this post with logs and config files - and also the full X11 error messages - once I am back at this machine, probably Sunday. If you need anything specific past the obvious culprits, please let me know, I'll put them up.

Thanks,

Flo

---

### Post by la_tupac on 2009-03-05
Hi you !! 
i have the same problem whith an ICH8 stripe raid.
the solution i found is the same as you. dmraid -ay and exit :)
but the busybox is not cool! i wanna boot normaly.
i tested whith the intrepid Kernel and it works !
i tested whith the intrepid dmraid modules and it dont.
So, the problem of dmraid activation is from the kernel !!!!
That's why i tryed to make my own one. I made a kernel whith initrd whitch dont works better.
I'm actualy trying to make it again whithout initrd and deleting dmraid package (dmraid will be in hard in the kernel)

my adress : [email]la_tupac@hotmail.com[/email]
plz send me a mail i you want help about this.

ps srry for my bad english :p
kisses to all !!

---

### Post by couillard45682 on 2009-03-14
> **la_tupac said:**
> Hi you !! 
i have the same problem whith an ICH8 stripe raid.
the solution i found is the same as you. dmraid -ay and exit :)
but the busybox is not cool! i wanna boot normaly.
i tested whith the intrepid Kernel and it works !
i tested whith the intrepid dmraid modules and it dont.
So, the problem of dmraid activation is from the kernel !!!!
That's why i tryed to make my own one. I made a kernel whith initrd whitch dont works better.
I'm actualy trying to make it again whithout initrd and deleting dmraid package (dmraid will be in hard in the kernel)

my adress : [email]la_tupac@hotmail.com[/email]
plz send me a mail i you want help about this.

ps srry for my bad english :p
kisses to all !!

Hi,
I had the same problem when i upgraded from Intrepid to Jaunty. The solution i found is to boot with dmraid -ay, exit; from busybox. When ubuntu succesfully booted, open a console and type this:
update-initramfs
update-grub.
It worked for me!:P

p.s. sorry for my bad english too ;)

---

### Post by la_tupac on 2009-03-15
Hi thank you very much but i'v already found it !!
Tanks again xD


Ubuntu rox !! i just love it ;)

---

