---
title: "random logging off since lucid upgrade"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by myotis on 2010-05-18
Just upgraded from Karmic to Lucid using auto upgrade on Thinkpad T42.

Since doing this, I am experiencing random logging off.

Suddenly, I get dumped to the log in screen and need to log back in.

A search in the forum suggests this was a problem that some people had with Karmic, but is now fixed (I never experienced it with Karmic) 

It seems to be associated with Firefox, with it not happened since switching to Chrome, but switching back to Firefox has just resulted in me being logged off. This could be a coincidence of course.

This is rather serious problem as I use the Thinkpad to give presentations, so I am hoping there is a solution that someone can point me towards.

Thanks,

Graham

---

### Post by malkdude on 2010-06-05
Hi Graham,

I was experiencing the same problems. Which graphics card do you have? I have an ATI Xpress 200m, which is a real pain... I upgraded ubuntu from karmic to lucid as soon as lucid was out. I didn't experience any problems in gnome, but after I installed the kde-desktop, I started experiencing random logging out. It usually happens when I'm opening some new window I think. The screen goes weird, and I see some vertical stripes of color for a second, and after that, I see the original screen for a split second, and after it takes me back to the login screen.

I thought it had to do with the graphics card driver. Please note that I had this problem with lucid kde but not lucid gnome. Also, I had the issue of seeing scrambled colors when I use Konqueror, at the starting page, after I try to select a region of the starting page. So I figured it had to do with the graphics card. After a few days of reading through the posts, I finally fixed it. Now it doesn't log out anymore by itself (at the expense of a few minor drawbacks). Here is what I did!

I disabled KMS, had ubuntu create an xorg.conf.new file, edited the file by disabling RenderAccel and setting the Acceleration method to "XAA" instead of the default "EXA". I also edited the grub file, and added a nomodeset option. I don't understand what this nomodeset option does though... But anyway, after doing all of those things, kubuntu stopped logging out by itself, and displaying those scrambled colors (it does display scrambled colors once though at the login, but only for 1 sec, so it's manageable). I'm not sure if all of those things were necessary, but since it took me so much time to fix, I thought I'd share it with you and others...

---

### Post by myotis on 2010-06-05
I'm not at all sure what graphics card my Thinkpad has. But I am now confident its a Firefox thing.

Since my original post, I have been using Chrome with not a single problem.  Every so often I will give Firefox a go and get the same problem (but after varying intervals. On one occasion being logged out as Firefox was launching, and on other occasions going for several hours before being logged out.

I have now uninstalled Firefox and re-installed it, to see if this improves things, but haven't yet had an opportunity to try it out.

Thanks,

Graham

---

### Post by frederickjh on 2010-07-16
I too am experiencing this random log offs on  a new install of Lucid. At first I thought that this was related to the LTSP server that is running on the machine. But it only affects me on the server. The client continue to run fine but I get logged out.

I have never seen it log me out. Normally I leave the computer and then come back to find myself at the login screen.

I am not sure if it is a Firefox problem as I use Opera as a web browser and am experiencing this as well.

This seems to be the last entry in messages from before I logged back in.


> Jul 16 10:00:45 henderson kernel: [10735.686443] opera[22568]: segfault at 76 ip 0805a7db sp bf8e4d80 error 4 in opera[8048000+ee2000]

I am wondering if this is related to how the segfaults are being handled and not any one program. Can any other also check you messages log  file to see if you have a segfault in the list before logging back in?

You can access the messages log file by going to System>Administration>Log File Viewer  then select messages in the left hand panel and then scroll to the bottom where the most recent messages will be.

Maybe together we can put some information together that will help solve this.

---

### Post by frederickjh on 2010-07-16
It looks like in the past this problem seems to have been related to problems with the screen saver. I am going to try turning it off and see what happens.

[http://ubuntuforums.org/archive/index.php/t-198361.html](http://ubuntuforums.org/archive/index.php/t-198361.html)

---

