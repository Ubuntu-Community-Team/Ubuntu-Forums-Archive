---
title: "i have a seagate 1TB portable hard drive that used to be able to mount and use till ."
date: 2017-04-06
forum: MINT
---

### Post by jenelle on 2017-04-06
i have a seagate 1TB portable hard drive that used to be able to mount and use till i downloaded drop box to send my photos to people that i need to , after i did that it stopped working which is annoying as i have put my photos onto it will see if a friend will let me put it on their computer if need be as i dont want to lose photos if possible but if i can fix with out losing would be great 

i did find a link to a possible fix but i am not 100% sure so i am asking you guys if you know the anser to fixing it the following comes up when i try 


> Unable to mount Seagate Expansion Drive

Error mounting /dev/sdb1 at /media/jenelle/Seagate Expansion Drive: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1001,gid=1001" "/dev/sdb1" "/media/jenelle/Seagate Expansion Drive"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

saturday it worked sunday it did not work 

[http://askubuntu.com/questions/512000/unable-to-mount-my-passport-1tb-hardisk-in-ubuntu-14-04](http://askubuntu.com/questions/512000/unable-to-mount-my-passport-1tb-hardisk-in-ubuntu-14-04)
not sure if this is an answer or not

---

### Post by yancek on 2017-04-06
The message you posted indicates the windows (ntfs) filesystem on that partition is in an inconsistent state.  Various possibilities referred to in the message but the most common is having the drive attached to a windows system, shutting down the windows system while still hibernated which is the default for windows 10.  Boot windows and do a full shutdown,  might also run chkdsk to be on the safe side.

---

### Post by jenelle on 2017-04-06
I'm new at that sort if stuff how do I do that

---

### Post by yancek on 2017-04-06
You should have options within windows to turn off hibernation and or fastboot and probably also in the BIOS.

Run the chkdsk /f command from windows at a Command Prompt which you should be able to access from the main menu in the lower left of the Desktop.

---

### Post by jenelle on 2017-04-07
only option are these

---

### Post by QIII on 2017-04-07
The answer indicated the operating system Windows from Microsoft.

Have you recently had your mobile drive connected to a Windows machine?

---

### Post by jenelle on 2017-04-07
no , i downloaded drop box and after that it happened

---

### Post by yancek on 2017-04-07
You're posting at an Ubuntu Linux forum but do not indicate which Linux or version of Ubuntu you are using.  That would be useful information.

How did you install dropbox, directly from their site at the link below?  If so, which download did you select?

[https://www.dropbox.com/install-linux](https://www.dropbox.com/install-linux)

I'm not sure why you posted the images above.  They are unrelated to the problem.  The initial error you reported indicate that the partition on the hard drive you are trying to access is in an unsafe state.  It also indicates that the filesystem on the partition is a proprietary microsoft windows filesystem yet you indicate you have not had it attached to any windows system.  Do you have a windows install on your computer?  If you don't and haven't attached that drive to another computer, I certainly would not expect to see that error although it might be possible.  

I've never used dropbox so don't know if it's possible to cause a problem like this.  And just to be clear, the suggested 'fixes' in the error output in your initial post will all have to be run from a windows system.  I'm not sure why you would use a windows filesystem if you don't have a windows OS installed?

---

### Post by jenelle on 2017-04-07
i did but then it told me i had it already in my packages wish i looked forst i did the 64 bit one

Ubuntu (.deb)	 	64-bit	 	
is one i down loaded but ended up using one in packages cause it said same one was there

> **yancek said:**
> You should have options within windows to turn off hibernation and or fastboot and probably also in the BIOS.

Run the chkdsk /f command from windows at a Command Prompt which you should be able to access from the main menu in the lower left of the Desktop.

just thought for a second did you want me to plug device in then open windows?? i didnt have it plugged in when i opened and screen shot the pages i was just looking for what you said to look for

found windows login in is this it ??

found this too have connected but still wont let me open it to get to my photos

---

### Post by jenelle on 2017-04-09
i decided to do what that link said and prayed it worked it looked like it did then i thought it didnt and then computer turned off and i had to boot it again and seems to have worked photos are still all there so all gone thank you for trying to help me

---

