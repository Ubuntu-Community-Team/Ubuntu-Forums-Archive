---
title: "How does 1 add local package to Ubuntu 16.04 install and make /boot FAT32?"
date: 2016-07-06
forum: Installation &amp; Upgrades
---

### Post by monkeyman_stones on 2016-07-06
I have recently purchased a Gizmosphere  Gizmo 2 Single Board Computer (SBC, which is an x86 64-bit processor computer) and am trying to install Ubuntu Mate 16.04 64-bit to my new SanDisk Extreme Pro MicroSD card.  To do so with only 1 card needed I must follow the directions of Timesys for installation of Ubuntu ( [https://linuxlink.timesys.com/docs/gsg/gizmo2](https://linuxlink.timesys.com/docs/gsg/gizmo2) ), but those instructions seem to be well out of date as 16.04 now completely prevents installation of Ubuntu with a FAT32 file system for (any partition, but to keep it relevant to this install -> ) the /boot partition, but I must have the /boot partition in FAT32 file System type for the board to boot (as the BIOS requires as much for booting from either the MicroSD socket or the mSATA III slot) without requiring an additional USB or SD  for placement of the /boot partition (by the Ubuntu instructions here: [https://help.ubuntu.com/community/BootFromSD](https://help.ubuntu.com/community/BootFromSD) ).

In addition I also need (must) to be able to add a local file (bzImage-3.12-ts-x86_64 Kernel which is included on the tiny MicroSD card the Gizmo 2 comes with) to the installation the Ubuntu installer performs (specifically bzImage-3.12-ts-x86_64 from the 4GB MicroSD which came with my new Gizmo 2).

So, I need to know how to install Ubuntu Mate 16.04 64-bit with the /boot partition in FAT32 formating, plus, I need to know how to install a local package/file/application for and during the installation of Ubuntu Mate 16.04 64-bit.

Feel free to ask me any seemingly relevant questions you need to aid you in answering these questions.


Thank you very much for your help and assistance,

David A.W.

Note: I've asked the same question on AskUbuntu and it was altered repeatedly by admins who made it so unlear that a group of AskUbuntu admins have blocked it completely, saying that it was not clear enough.  I added clarification and am now adding a link to that post here: [http://askubuntu.com/questions/795664/how-to-add-a-local-file-kernel-to-ubuntu-mate-16-04-install-and-make-boot-fat](http://askubuntu.com/questions/795664/how-to-add-a-local-file-kernel-to-ubuntu-mate-16-04-install-and-make-boot-fat) .  It is a chalange to read and follow due to repeated, severe alterations by AskUbuntu admins (or users) which made it's purpose unclear.  So, to clarify here:
The GizmoSphere Gizmo 2 SBC requires a FAT32 /boot partition to allow the BIOS to recognize it without other actions from the user. In addition, to enable the BIOS to allow booting from the single disk without the user having to take extra steps every single time they boot and/or reboot, the bzImage-3.12-ts-x86_64 kernel which is included in the Timesys OS MicroSD card which comes with the GizmoSphere Gizmo 2 must also be installed in /mnt to allow the Gizmo 2's BIOS to boot a linux distro when having pressed the power button.  Because of the reasons above, booting my Gizmo 2 (or anyone else's Gizmo 2) from it's MicroSD slot containing Ubuntu requires multiple steps from me and I had to buy an additional USB SD card reader, a small (in storage space but full size) SD card and a USB splitter to allow me to have the keyboard, Mouse and USB SD Card reader all plugged into the USB 2.0 ports at the same time (The Gizmo 2 Bios does not allow function of the USB 3.0 ports until after an OS is booted, so they cannot be used for the additional USB SD card reader which is absolutely required because no one has informed me how to overcome the issues presented here).  This is important because a Gizmo 2 user would have to pull their /boot USB SD card reader and it's SD after booting to allow for the use of the USB 2.0 port for a mouse, which becomes an enourmous problem upon package and/or system update because the USB Card Reader must be reinserted to allow whatever changes to the /boot partition the update includes.  That means that they cannot use (without a USB hub) a graphical package manager such as Synaptic or Ubuntu Mate's "Software Updater" because when questions or additional actions pop up for the user to respond to, they must unplug their USB SD Card Reader to insert their mouse, but upon clicking whatever required as much that package manager will go straight back to continuing the update and the /boot partition on the SD card will not be present because it had to be removed to allow the use of the mouse.  So due to the setup of Ubuntu Installer, Gizmo 2 owners cannot easily update their OS, or cannot use Ubuntu at all. This, becuase Ubuntu will no longer allow a /boot partition to be formated in FAT32 and does not provide a way to add another local package to it's installation.
 The other Linux distro listed in the instructions by Timesys above, does boot with a single disk with some special tricks during it's install. But I strongly prefer Ubuntu as I know it much better than the other distro with the same name as a hat. 

I hope this clarifies why this question is important and needs an answer, as it will allow users of the GizmoSphere Gizmo 2 x86 SBC to use Ubuntu as their OS without risk or issue.

Thank you again and once again, feel completely free to ask any question you feel is important for resolution of this issue as it involves all Gizmo 2 owners wishing to use Ubuntu beyond 12.04 (and with extreme work, Ubuntu 14.04).

David

---

