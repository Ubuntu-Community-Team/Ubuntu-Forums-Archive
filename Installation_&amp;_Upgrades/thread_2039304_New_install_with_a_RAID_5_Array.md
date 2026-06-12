---
title: "New install with a RAID 5 Array"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by snuffy47 on 2012-08-08
Hello

I have a system loaded on a 20GB drive and a RAID 5 storage setup on separate discs but it is using Ubuntu for the RAID setup

If I was going to reload the ubuntu drive will it reconize the RAID setup?

---

### Post by darkod on 2012-08-08
If you use the Alternate CD it should by default because it has built-in software raid support.

If you use the standard desktop live cd, first you will need to boot it into live desktop, add the mdadm package in the live environment, and maybe activate the array. Not sure about this last one. Only after that start the installer from the icon on the live desktop and it will see the array.

If you ever want to activate existing mdadm array for any reason, be sure to use the --assemble command and not the --create command. The --create is used only the first time. If used later on existing array it can recreate it as new and delete the data.

---

### Post by snuffy47 on 2012-08-08
Okay i think I understand this correctly

Just to add some more information currently I have been using a separate server running server edition 10.04 ubuntu and then another computer for my media center.

Being my media center computer is on almost 100% of the time anyways I would like to stop using the Server remove the 5 disk dock that the storage disks are in and then make 1 computer to run both media and server functions.

It sounds to me that I will be okay to do this if I install Ubuntu and ensure madin is installed and then attach my storage media that was already configured with ubuntu in Raid 5.

---

### Post by darkod on 2012-08-08
The beauty of linux software raid is that you can easily move it to another machine.

If I understand you right, that's what you would like to do. It should be OK.

As I said, you might need to assemble the array the first time after the move, but that is easy when all your disks are OK.

If you install the Server version, or the desktop using the Alternate CD, the software raid is recognized automatically.

Only the desktop live cd doesn't include the mdadm package.

---

### Post by snuffy47 on 2012-08-08
That is sweet

You are correct I want to take my 5drive in 3 bay module and move it to another machine.

The server currently has the os running on another drive :)

this will save me trying to move 1TB of movies off the array :)

---

