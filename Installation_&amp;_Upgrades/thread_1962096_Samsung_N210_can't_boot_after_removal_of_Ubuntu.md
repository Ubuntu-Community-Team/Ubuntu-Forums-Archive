---
title: "Samsung N210 can't boot after removal of Ubuntu"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by Davidovic on 2012-04-20
Dear all,

I have a problem with a Samsung N210 Plus netbook:

The netbook came preinstalled with Windows 7 Starter.
I am new to Linux and recently I installed and tried out several different distro's. I installed them next to Windows 7, leaving each on its own partition. The last one I tried was Ubuntu.
Every time I tried out a new linux distro, I erased the Linux partition (from within Windows), restarted the netbook and installed from a live-usb (created with Unetbootin). That all worked fine.
Now I wanted to remove Ubuntu and have only windows again (because the netbook is my wife's, and she doesnt want me to mess with it :smile: ). So once again I erased the Ubuntu partitions from within Windows. I restarted and now I'm stuck.

I get a black screen saying:
```
error: file not found
grub rescue>
```

Whatever I do, I can't get past it. I can't start any live-usb's anymore either. I've checked the BIOS, and USB is set to be the first boot device.

Normally the Samsung netbook has a recovery system, reachable by pressing F4 during boot, but this doesn't work.

I've read dozens of threads about this/similar problems, and tried out all kinds of "bootable-usb-tools", but the thing is that the netbook just doesn't seem to read it. It keeps saying "error: file not found
grub rescue>" and it does nothing else.

The last time I turned off the netbook was from Windows, so I suppose the Windows partition should be fine, I just can't get it started anymore.

Does anybody have an idea on how to solve this?

Thanks for any help! (And for saving my marriage ;-) )

---

### Post by darkod on 2012-04-20
Double check the boot options to boot from USB, and recreate the usb stick again if necessary. You will need to make it boot from the usb into ubuntu live mode.

After that the fix is easy.

From ubuntu live mode, you can install generic MBR with lilo, and that will boot windows without issues. On another note, be careful about using the recovery partition (even if you can get into it) because that usually means deleting all of the hdd including the data. I think that's grounds for a divorce. :)

Once you manage to get into ubuntu live mode, the lilo procedure in terminal is:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be warning message about lilo configuration, IGNORE IT. Just continue. You will be using only part of lilo anyway and the warning is nothing.

Note that this procedure will make windows boot directly, there will be no option for ubuntu. That is what you want if I understand right.

---

### Post by Davidovic on 2012-04-20
hello darkod,

Thanks for your quick reply. I've checked the BIOS again, and all USB-entries are above the HDD. I also created the live-usb once more, the same way I always did it, and no difference. Before I entered this forum I also tried live-usb-versions from other linux distro's as well, all with the same result :-/ Nothing boots.

BTW I'm not worried about data loss. All personal files were synched with dropbox, so all I need is to get Windows 7 working again, one way or another. Any other ideas?

Unfortunately I have to leave now, so I won't react within the next few hours, but I'll get back for sure!

---

### Post by darkod on 2012-04-20
Sounds like the usb is not bootable.

If you are sure the usb is bootable and fine, you are really stuck. I don't know of a way to do this without booting from either cd or usb.

One option is creating win7 bootable usb stick, and see if that boots. If it does, you will be able to do a repair option that will repair the boot.

Also, you can use Boot-Repair to write windows bootloader, but again, you will have to boot it either from cd or usb.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Nikhil Parmar on 2012-04-20
How to repair and reboot to Windows 7:
 a) Insert the Windows 7 System Repair DVD or Installation DVD and reboot.
 b) Select the correct keyboard input method and click ‘Next’.
 Note: If you are using the Windows7 Install DVD then at the 'Install  Now' prompt (Do not pick the Install Now option) instead choose the  'Repair your computer' option located in the lower left of the dispay.
 c) The System Repair tool will search for a valid operating system  and will report that “Windows found problems with your computer’s  startup options. Do you want to apply repairs and restart your  computer?”
 d) Click ‘Repair and restart’ and reboot again to the Windows 7 System Repair environment.
 e) Click ‘Next’ at the keyboard selection prompt and when the ‘System  Recovery Options’ screen appears verify that the “Use recovery tools  that can help fix problems starting Windows” is selected.
Note that on your Dual Boot system there now should be only one operating system listed. Click the ‘Next’ button.
 f) Now from the menu list select the ‘Command Prompt’ option.
 g) At the DOS prompt type the following three commands:
 bootrec.exe  /fixmbr
 bootrec.exe  /fixboot (may return an 'Eliment not found' message)
 bootrec.exe  /RebuildBcd
 h) Close the command prompt window and click the ‘Startup Repair’ option.
 i) The repair process may take some time, so wait until the process  completes at which point you will see two messages “Windows cannot  repair this computer automatically” and “Startup Repair cannot repair  this computer automatically”.
 These messages are the result of the radical changes made by removing the other drive. Ignore the Send/Don’t send options.
 J) Close this message window by clicking on the X in the upper right  corner of the Send/Don’t send window. Next click on the ‘View advanced  options for system recovery and support’ option and from the main menu  once again click ‘Startup Repair’. This time  the repair process may only that a few seconds and when prompted  “Startup Repair could not detect a problem”, click ‘Finish’  and run the  ‘Startup Repair’ option one more time, click ‘Finish’, and then remove  the System Repair DVD and click ‘Restart’.  Reboot  the computer.
........Hope this helps you......:p

---

### Post by Nikhil Parmar on 2012-04-20
If few steps of the above doesnt happen, jut skip and move ahead for further steps.
I had the same prob. but this solved. Hope this solves ur prob too. :-)

---

### Post by Davidovic on 2012-04-20
Darkod, you were right, the usb-stick was not bootable. I don't understand why, because I created bootable usb's with Unetbootin several times, and it always worked.
Now I used instructions on the Ubuntu website for creating a live-usb through the Terminal (on the Mac, which I'm on now). With that one I was able to reinstall Ubuntu.

After reinstallation I followed your instructions on lilo, for fixing the MBR. When that was done, the netbook started into Windows again, and from there I removed the linux-partitions. All nice and clean again!

When I get myself a laptop, I'll continue playing with linux :-D

Thank you very much for you help!

---

### Post by darkod on 2012-04-20
No problem. You could have done all of that directly from live mode (Try Ubuntu), without needing to install ubuntu again. But anyway, you got it sorted out.

You can mark the thread Solved in Thread Tools above the first post.

PS. Sorry, it already is marked. Didn't see it.

---

