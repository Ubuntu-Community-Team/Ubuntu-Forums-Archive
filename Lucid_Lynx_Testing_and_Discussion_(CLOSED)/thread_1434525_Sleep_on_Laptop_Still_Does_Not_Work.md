---
title: "Sleep on Laptop Still Does Not Work"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by needhelp123 on 2010-03-20
Lynx is unable to compete with Windows due to the fact that on Windows you can just close the laptop lid and open it up again to be greeted by the login screen whereas on Lynx you are greeted by a blank screen to which the only possible option is to restart.

I just tried the beta today and this is my reflection.

---

### Post by lavinog on 2010-03-20
> **needhelp123 said:**
> Lynx is unable to compete with Windows due to the fact that on Windows you can just close the laptop lid and open it up again to be greeted by the login screen whereas on Lynx you are greeted by a blank screen to which the only possible option is to restart.

I just tried the beta today and this is my reflection.

Did it work in karmic?
What video card do you have?

---

### Post by seenthelite on 2010-03-20
I have found I can get sleep to resume by using ctrl+alt+F1 the first time I try to use it after a reboot. Then sleep and resume works normally until I reboot then ctrl+alt+F1 again. May work for you.

---

### Post by Starks on 2010-03-20
This bug may be of interest to you.
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/496842](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/496842)

---

### Post by needhelp123 on 2010-03-20
> **lavinog said:**
> Did it work in karmic?
What video card do you have?

1. No, it has not worked on any Ubuntu edition, with any available fix.
2. ATI

---

### Post by lavinog on 2010-03-21
Do you know the actual video card?
is it a radeonhd 2xxx 3xxx 4xxx or other?

The issue may be caused by the radeon driver.

Something to try is to disable KMS: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)



Funny thing is, a google search showed some posts with the same symptoms...with one exception...it is happening in windows:
[http://forums.amd.com/game/messageview.cfm?catid=260&threadid=122679](http://forums.amd.com/game/messageview.cfm?catid=260&threadid=122679)
[http://social.technet.microsoft.com/Forums/en-US/itprovistahardware/thread/00f8a726-c4f8-4873-b235-d59259563a0a](http://social.technet.microsoft.com/Forums/en-US/itprovistahardware/thread/00f8a726-c4f8-4873-b235-d59259563a0a)

If you are using a recent card, you might be able to try the fglrx driver...in the past I was able to get my laptop to sleep with fglrx, but then ati dropped support for my card (200m).  Now that my card is required to use the radeon driver, I have had the same symptoms you described.
The thing about the radeon driver is that development is moving fast for it, but I think sleep and hibernate is lower on the priority list.  Getting 3d support for newer cards is.
It has been mentioned on the forums that using the latest version may fix this issue (even though lucid is in beta, it doesn't mean that everything is the latest version)
lucid's version: 1:6.12.191
latest version: 1:6.12.192

---

### Post by needhelp123 on 2010-03-21
> **lavinog said:**
> Do you know the actual video card?
is it a radeonhd 2xxx 3xxx 4xxx or other?

The issue may be caused by the radeon driver.

Something to try is to disable KMS: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)



Funny thing is, a google search showed some posts with the same symptoms...with one exception...it is happening in windows:
[http://forums.amd.com/game/messageview.cfm?catid=260&threadid=122679](http://forums.amd.com/game/messageview.cfm?catid=260&threadid=122679)
[http://social.technet.microsoft.com/Forums/en-US/itprovistahardware/thread/00f8a726-c4f8-4873-b235-d59259563a0a](http://social.technet.microsoft.com/Forums/en-US/itprovistahardware/thread/00f8a726-c4f8-4873-b235-d59259563a0a)

If you are using a recent card, you might be able to try the fglrx driver...in the past I was able to get my laptop to sleep with fglrx, but then ati dropped support for my card (200m).  Now that my card is required to use the radeon driver, I have had the same symptoms you described.
The thing about the radeon driver is that development is moving fast for it, but I think sleep and hibernate is lower on the priority list.  Getting 3d support for newer cards is.
It has been mentioned on the forums that using the latest version may fix this issue (even though lucid is in beta, it doesn't mean that everything is the latest version)
lucid's version: 1:6.12.191
latest version: 1:6.12.192

My drivers are latest version and I have tried turning off KMS, doesn't work.

---

### Post by sdowney717 on 2010-03-21
I know its different. I just tried putting my desktop to sleep. It worked.
To wake it up, press the power button. Login and it is all back up.

---

### Post by zoomy942 on 2010-03-21
mine works when i use the sleep button.  but the lid closing does nothing

---

### Post by michaelzap on 2010-03-21
Neither Sleep nor Hibernate worked on my Lenovo Y530 in Karmic x64, and they still don't in Lucid beta x64. But I feel like there's been some progress, because now they don't work in a more interesting way. My laptop does seem to go to sleep when I choose that from the Shutdown menu, but it never wakes up again. That's something, anyway.

Also: I've set it to only dim the screen when the lid is closed, but instead it insists on logging me out (which is kind of annoying, since at least in Karmic I could shut the lid - it didn't sleep but at least it didn't log me out).

Dunno why, but I do feel a little more hopeful that this will get resolved in Lucid even though it didn't in Karmic.

---

### Post by kyleabaker on 2010-03-21
My laptop won't sleep or hibernate properly (HP dv1000).

My desktop (AMD Athlon 64 X2 6000+) will sleep properly and resume (only from power button, not mouse or keyboard), but it won't resume cleanly from hibernate mode. After resuming from hibernate mode, the graphics (nvidia) are corrupt to the point of not being usable at all, but the system is properly resumed (I can use keyboard shortcuts to open apps to confirm that it resumed, and power+enter to shutdown properly).

---

### Post by arich57 on 2010-04-09
> **lavinog said:**
> Did it work in karmic?
What video card do you have?

Mine use to in Karmic but doesn't in beta1. Nvidia quadro video card. I'm more then will to try any ideas.

Thanks,

---

### Post by djchandler on 2010-04-10
Suspend works on my laptop. I don't hibernate as a general rule, so that I have no idea about. And what hardware we are talking about does make a difference.

The OP over generalizes without giving specifics. And how the computer is put to sleep, what events wake it up, etc., are end-user configurable. More people need to spend a little time with their hardware owners' manuals before they make posts. At the very least, give us the enough information to help solve the issue.

---

### Post by arich57 on 2010-04-10
> **djchandler said:**
> Suspend works on my laptop. I don't hibernate as a general rule, so that I have no idea about. And what hardware we are talking about does make a difference.

The OP over generalizes without giving specifics. And how the computer is put to sleep, what events wake it up, etc., are end-user configurable. More people need to spend a little time with their hardware owners' manuals before they make posts. At the very least, give us the enough information to help solve the issue.

I'm using the gnome power management to have my laptop sleep when the lid is closed on battery power.

I can see the wireless get shut down and it seems like everything is working (music stops playing, etc) but the display goes black but not off.

It's like it has hung somewhere. This ends up killing my battery.

I'm upgrading to beta 2 right now. I'll let you know how it goes.

If there is anything I can provide to help, let me know.

---

### Post by zoomy942 on 2010-04-10
my beta 2 still doesnt work.

---

