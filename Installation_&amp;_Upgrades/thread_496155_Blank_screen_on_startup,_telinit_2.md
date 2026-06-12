---
title: "Blank screen on startup, telinit 2"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by paborden on 2007-07-08
So I'd installed Feisty on an older Dell Dimension 2350 desktop. However, when starting up, I'd get a blank screen and nothing more.

Someone suggested hitting ESC, starting in recovery mode, and using the telinit 2 function to get up an running. This worked perfectly.

BUT, now whenever I go to start up I have to do this. Thus I pretty much never turn the computer off. I'd like to fix this problem for real and get the system booting normally. Any suggestions?

Thanks for your help everyone.

---

### Post by Mugatu on 2007-07-10
> **paborden said:**
> So I'd installed Feisty on an older Dell Dimension 2350 desktop. However, when starting up, I'd get a blank screen and nothing more.

Someone suggested hitting ESC, starting in recovery mode, and using the telinit 2 function to get up an running. This worked perfectly.

BUT, now whenever I go to start up I have to do this. Thus I pretty much never turn the computer off. I'd like to fix this problem for real and get the system booting normally. Any suggestions?

Thanks for your help everyone.

**I have the same exact system and the same exact problem.  this is how i solved it:**


"Edit the file /boot/grub/menu.lst and find the line that starts with "# kopt". In my case:

# kopt=root=UUID=73014da7-ff55-487e-bdbc-4ad6d47e5d68 ro

Add "vga=773" to the end of the line. So in my case:

# kopt=root=UUID=73014da7-ff55-487e-bdbc-4ad6d47e5d68 ro vga=773

Save the file. Now run "update-grub". The next time you boot, you should see the splash screen!"


from:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/68012](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/68012)

---

