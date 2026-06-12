---
title: "Black Screen"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by nadazip on 2008-04-26
Come on guys/gals i have been looking through all the threads and there are so many unanswered posts on this subject.

My computer boots to black screen

reboot enter rescue mode - fix xserver - boot

boots into some messed up low res version 

reboot it boots back into messed up version 

enable nvidia restricted driver reboot black screen again.

Is this something that is being worked on? Do i just need to wait? Have i missed a huge flashing neon sign with the answers.

I have just seen new user posts asking for help on this subjest that have just gone unanswered.

Please just advice. I have given up a lot for linux, but i am prob not going to just go low res single monitor.

If ATI works let me know i will buy a new video card i just want my system kind somewhere back to where it was 48hrs ago:)

Thanks peeps

nadazip

---

### Post by alsoknownas on 2008-04-26
Having this problem too... :(

My explanation as to what I did: [http://ubuntuforums.org/showthread.php?t=768590](http://ubuntuforums.org/showthread.php?t=768590)

---

### Post by Pumalite on 2008-04-26
Explain to us better what you did. Upgrade? Clean install? System just stopped working?

---

### Post by nadazip on 2008-04-26
I just did the upgrade.

---

### Post by Pumalite on 2008-04-26
Try sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver. Then: startx

---

### Post by nadazip on 2008-04-26
I do not get the option to choose the video driver in the xserver. Just get the kb and mouse options. 

I see there has bee a couple of newer threads on the smae subjet.

---

### Post by Pumalite on 2008-04-26
I've seen them. Do you see Grub at all?

---

### Post by nadazip on 2008-04-26
What do you mean? In the xserver config?

---

### Post by Pumalite on 2008-04-26
At boot.

---

### Post by nadazip on 2008-04-26
I am not sure what you mean. My computer boots upt to the point of the ubuntu studio logo and then goes black when it should be the log in screen. However if i hit escape when initializing i can boot into rescue mode.

---

### Post by Pumalite on 2008-04-26
This could be due to improper UUID's in fstab.
Run: blkid and compare with /etc/fstab.

---

### Post by nadazip on 2008-04-26
Not sure if that did anything i typed it and then it just wen to the next command line.

Let me know what i should do next.

Should this not be some kind of main thread titled black screen. as every minute goes by it seems there is a new post that seems to be people with same problem. I feel certain we need to get the restricted driver working. Is this not the case.

---

### Post by nadazip on 2008-04-26
I wish i did not have to deal with this as i had other projects planned for this weekend. I may sound like a slacker but i have worked on this problem and dedictaed much time to it before. I am going to reinstall feisty ubuntu studio and envy. That worked perfect.

Does anyone have any solution that is not just stbbing in the dark before i leave i do not want to go back but i just cant deal with this anymore.

---

