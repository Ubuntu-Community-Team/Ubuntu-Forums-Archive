---
title: "Ubuntu 11.10 VirtualBox Host - Problems installing Ubuntu guests"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by ajveach on 2012-04-15
I purchased some new hardware recently with the intention of setting up a VBox hosting system that will let me run some development servers along with servers for other tasks (MySQL, Apache). I had no problems with the installation of Ubuntu 11.10 server on my new server. I then was able to get VBox up and running to the point that I was able to start creating VMs.

When creating my first VM I gave it 2GB of memory, 150GB HDD, and I mounted the same 11.10 Server image I used for the host machine. In the process of installing ubuntu, there were a couple errors, but when I restarted the process everything went through. I was then able to login to the VM using RDP and set it up with SSH and MySQL. That machine is running just fine.

I then tried to create a small server to run Minecraft Server. I gave it 512MB of memory and 15GB HDD. Using the same 11.10 server iso, I started that machine up. When going through the installation process I received many different errors. (I will be listing some of them at the end of this post) Sometimes the loader would get all the way to installing GRUB, but would fail at that point. Sometimes it would fail as early as the timezone selection. It would also fail in different ways... sometimes just a blank screen while others it would say a specific piece of the installation failed.

I am now trying to skip that VM and make an apache server. I have created the VM with the exact same specifications that I used for the MySQL server. When I ran the installation I received an error message "Failing while unpacking packages". I tried a few times and wasn't able to get past that point. What was interesting is that it happened at different stages of the unpacking process each time.

I'm starting it again now as I'm writing this post to describe in more depth what's happening. As I started the VM again, I received a black screen telling me there was a segmentation fault. I assume this means that due to previous writes to the HD the installation can't proceed. I am now creating a new HD and mounting it in the original one's place.

I just started the VM again and got to the stage to install the base system. I have received this error message:

Debootstrap warning
Warning: file:///cdrom/pool/main/eeglibc/libc6_2.13-20ubuntu5_amd64.deb was corrupt

I received this yesterday as well. I have checked the ISO's integrity both during the installation process and using the md5sum. I have downloaded the file 3 times, each passing inspection.

After hitting continue from that error I receive this error:

Debootstrap warning
Warning: Couldn't download package libc6 (ver 2.13-20ubuntu5 arc amd64)

After a few more errors like that the installation completely failed.

I reset the machine and began again. This time on the "Loading Additional components" stage, the installer hung at 1% (Retrieving base-installer). When this happens the screen just sits at that stage indefinitely.

Reset the machine again. It's past the 1% where it hung last time, but at some point after 50% it gives me an error message saying there was trouble reading from the CDROM. I restarted the machine, and am checking the disc integrity. The integrity check failed. This made me realize that the iso was writable by the user. It doesn't seem like the installer would even attempt to write to the installation media, but to be safe I downloaded the ISO again and set the permissions to 644 and made root the owner (I am not using VBOx as root).

I mounted the new image that is not writable my my VBox user to the VM, and I'm starting the VM again. I selected English and checked the disc for defects. The disc is valid. After a reboot I started the installation process and.... it worked! No errors this time. Maybe the ISO permissions were the issue.

Since I was in the process of writing this up as I was troubleshooting, I'll leave the post and mark as SOLVED. Hopefully it helps someone else out down the road.

---

### Post by ajveach on 2012-04-15
It looks like I was wrong. I have gone back to make another VM, and I'm running into the same old problems.

I tried creating a new VM that is identical to the previous one that worked, but with only 512MB memory and 10GB HDD. I'm using the same ISO as the previous installation. I tried running the installation and got a variety of errors. Some were complaining about not being able to access files. After that I checked the disk again, and I'm told it's invalid. I've tried resetting the machine, and I can't even get the disk checker to run anymore. It's currently hung at 18%. 

Going to try walking through this as I write the post again.

I stopped the VM, and started it again. I modified the memory to 2GB for now to make it match the machine that worked. I'm connected on RDP. I went to "Check disc for defects" and the screen went black. It's stuck. I reset the VM. Tried to check the disk and got the same result: black screen.

I stopped the VM and removed the ISO from the IDE Controller. I added it back in and started the VM. I was able to get to the actual process of checking the disc this time, but I'm told that the ./pool/main/n/nmap/nmap_5.21-1.1_amd64.deb file failed the MD5 checksum verification. The funny thing is that when I was able to check the disc a few minutes ago, it was past this point and another file failed the check. It seems that files just aren't being read properly from the ISO, but it is in fact a valid image.

---

