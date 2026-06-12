---
title: "Re-installation problem"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by J Harp on 2013-04-21
My 12.04 install has become slow and balky. I have downloaded the latest 12.04.2 ISO file to reinstall, but I can't get md5sum to check it. When I follow the instructions in "How to md5sum" I get nothing but error messages.

Can someone give me a (preferably graphical) method to verify the ISO file? I''m no good at typing long entries into the command line, so a click by click would be good. Thank you.

Jim

---

### Post by kevdog on 2013-04-21
Hmm -- the only way I know how to check is through command line where you type:
md5sum <name of iso image>

If the iso image is so corrupted, possibly you'll get an error, however I've never exactly seen this.

---

### Post by J Harp on 2013-04-21
I tried that, got the msg. no such file or directory. When I do whereis ubuntu-12.04.2-desktop-i386.iso, I just get the file name back.

When I downloaded, I saw no option to send the download to a folder or directory, it just went into downloads. If there is such an option which I missed, I'll remove that download and try again.

Thanks for your response.

Jim

---

### Post by J Harp on 2013-04-23
Anyone have any pointers on how to do this. The instructions I found in 'How to md5sum" wouldn't work for me. Thanks

Jim

---

### Post by mörgæs on 2013-04-23
Please post the exact command you tried.

---

### Post by grahammechanical on 2013-04-23
May I suggest that you burn the ISO image to DVD/USB and run it. If it works, then it works! I have never checked the md5sum and I have tested many ISO images of the development release. I have had failures due to bugs in the Live session and in the Installer but never due to a bad download.

OH, by the way, when you ran that command to get the ms5sum of the ISO image were you in the Downloads directory? Did you cd Downloads?

Regards.

---

### Post by J Harp on 2013-04-23
Morgaes; Sorry, don't have the keyboard characters handy to properly spell your name.

the command I used was [COLOR=#333333][FONT=UbuntuMono]ubuntu@ubuntu-desktop:~$ cd Downloads. also tried md5sum ubuntu-12.04.2-desktop:~$ cd Downloads.

I just stick with plain old Ubuntu, too many varieties of things are confusing to me, I'm easily confused anyway. Mostly I just use it and don't tinker with it unless necessary. I'm not really comfortable with using the command line.

grahammechanical;

cd downloads is on the end of both the commands listed above. Should I do cd downloads as a separate command before going to md5sum? In one of my previous installs, I had to make 3 CD's to get one that would work, I did md5sum on one which worked.

Thank you both

Jim


[/FONT][/COLOR]

---

### Post by mörgæs on 2013-04-23
The command should be ```
md5sum ubuntu-12.04.2-desktop.iso
``` or something like that. 

If you stand in the download directory, write for example ```
md5sum ubuntu-12
``` and push the TAB key then the rest of the word appears automagically (provided you don't have files with a similar name in the directory).

---

### Post by J Harp on 2013-04-23
Thanks, I like that automagic stuff, especially when it does what I want it to do. I'll give it a try a bit later.
 
I'll try the install  when I get an up to date backup done, whether I get the file image verified or not.

Jim

---

