---
title: "Internal mic not working Aspire one"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DavidOC on 2009-10-05
I'm currently using Ubuntu 9.10 beta on my Acer Aspire One and I can't get the internal microphone to work with any application other than Sound Recorder.

I've made sure the input volume in Sound Preferences is set to the highest but I don't get any feedback from the input level unless I give the mic a hard tap.

The microphone works perfectly only in Sound Recorder but not in Skype 2.1 or any other application.  I've noticed that if I open Sound Preferences with Sound Recorder already open, the mic won't record any sound, even the input level in Sound Recorder drops to nothing.

Has anyone been experiencing this or have found any fixes to this problem?

---

### Post by woodybrando on 2009-10-19
yup, having the same issues with karmic and acer aspire one d150 internal mic. The mic only works in sound recoder. 

I had skype working in jaunty but haven't gotten it working in karmic yet. even updated to the latest kernel 2.6.32rc5 and it's still not working. 

i also just installed karmic on an eeepc 1005ha for my friend. had the same exact problem with the mic not working in anything but sound recorder. But when I installed the 2.6.32rc4 kernel and rebooted the internal mic did work in skype. I haven't tried rc4 yet on my aao d150. You can find the ubuntu team's kernel debs here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc4/)

to install cd to the directory you downloaded the header and image files in then type

sudo dpkg -i linux*

I received an error both times about the linux headers package but ignored it and rebooted and things seem okay except the internal mic still didn't work on the aao d150 while it did work on the eeepc 1005ha.

edit:
also tried to install  the rc4 kernel on the aao d150 and still no mic audio in skype. Also never figured out howto get around the linux-headers having a dependency on the exact version of linux header that I'm trying to install.

good luck
jayson

ps - random tip I learned today sudo tasksel is the easiest way to install server software on your ubuntu pc.

---

