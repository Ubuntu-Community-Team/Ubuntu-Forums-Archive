---
title: "Dual boot doubt"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by acb2000 on 2013-06-09
Hello, I have a doubt about dual boot. 
I have a old, really old, acer computer. It came with Windows XP but it was painfully slow and the computer taked literally 20 minutes just to start. Because of that I decided to install ubuntu on it. At that time I decided also to leave Windows on the computer because I was giving it to my uncles and I tought that they would want to use Windows from time to time. But I was wrong, they never used Windows and only ubuntu. My doubt is, now that I've installed ubuntu in dual boot with Windows, can I remove Windows completelly without the need to reinstall ubuntu?

Thanks! :D

---

### Post by Mark Phelps on 2013-06-09
If you truly have Windows and Ubuntu installed in separate partitions, then you can do the following:
1) Boot into Ubuntu
2) Launch GParted
3) Use it to reformat the Windows partition -- to use it for data storage
4) Open a terminal and enter "sudo update-grub".  This will regenerate the GRUB config file, and since only Ubuntu will be on your PC, it will boot directly into Ubuntu after you reboot it.

---

