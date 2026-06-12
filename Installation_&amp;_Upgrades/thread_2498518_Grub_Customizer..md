---
title: "Grub Customizer."
date: 2024-06-17
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2024-06-17
I have images that I want to use as backgrounds in grub customizer, I have renamed them to .png from .jpg and tried different sizes, but they just don't display on grub.  any help would be greatly appreciated.

Henry

PS Not sure if this is the right thread, move if needed.

---

### Post by Dennis N on 2024-06-17
Probably no reason to use grub customizer (which many say you should not use) for this. If you just want to change the background image for the default grub menu, the easiest way is to add a line in /etc/default/grub with a path to the image. As done here:

```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/home/dn/Pictures/grub-mesh-gradient-1.png"

```

Run sudo update-grub afterwards to have it take effect.

---

### Post by Hewjr100 on 2024-06-17
That I will do, thank you so much.

Henry

---

### Post by Rubi1200 on 2024-06-17
Grub Customizer is not something that is generally recommended to use. We have seen many, many posts here from users who have run into issues with it.

As **Dennis N** pointed out, with some tweaking, you can customize GRUB pretty much as you like without the use of an app.

If the solution provided resolved your question, please mark the thread Solved so others can find and use this method.

---

### Post by Hewjr100 on 2024-06-18
Just noticed your response, sorry for the delay.  Luckily I have been using it for years without any issues, other than the background image.  Anyway thanks for your info. I will keep it in mind.  Always good to read both sides of an issue.

Henry

---

### Post by Hewjr100 on 2024-06-19
So you all know I marked as solved, but nothing worked.  I will contact the maintainer and see what he say's.  Again I do appreciate all your help.

Henry

---

### Post by Rubi1200 on 2024-06-19
What do you mean by nothing worked?

The background image? Something else?

---

### Post by Hewjr100 on 2024-06-19
The background.  I believe the maintainer changed the type and size of the image, this is ther info I am looking for.  I did at one time find it, but now I can't.

Henry

---

### Post by ajgreeny on 2024-06-19
You need to use images with some specific properties as a background for the grub menu; you can not simply use any image you happen to have on your system.

See [https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays) for all the details and then simply copy that chosen image to **/boot/grub** and run ***sudo update-grub***

PS:
I have never used Grub-Customiser, nor seen any reason to do so. It is simple enough to do anything you need with exits of the simple text config files.
Ask here for details of something specific if you can't find it.

---

### Post by Rubi1200 on 2024-06-19
Check the link posted by **ajgreeny **as there is good information there.

In my testing, you can also place the image in your home folder. I used the Pictures folder.

The most important thing, however, is the image size. It needs to match your screen resolution. 

For example, on my laptop it is 1366x768. If you use a larger image it won't display at all and if you use a smaller one it won't render correctly.

Try testing with a few images and let us know what worked.

---

### Post by Hewjr100 on 2024-06-20
Looking at it now, will update later.

Henry

---

### Post by Hewjr100 on 2024-06-20
Thanks for the link working on it now.

Henry

---

