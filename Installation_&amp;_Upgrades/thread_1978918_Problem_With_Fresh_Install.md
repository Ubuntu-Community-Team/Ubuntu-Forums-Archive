---
title: "Problem With Fresh Install"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by enigma55 on 2012-05-12
This morning, I burned Ubuntu 12.04 LTS 64 bit to a dvd on osx. I Then went to install it on a old PC with a quad core. It shows the initial brown screen with the keyboard at the bottom, goes black, then shows the ubuntu loading screen. Then it goes black again and reads "BusyBox v1.1...." and "(Initramfs) unable to find a medium containing a live file option". 

The hard drive is not clear, and is currently very full. I was planning on formatting in the ubuntu installer. Is that the problem? If so how can I format it? The current OS is corrupted.

---

### Post by Rubi1200 on 2012-05-12
I would check the integrity of the image first and then consider burning also at the lowest possible speed for best results:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by darkod on 2012-05-12
I might be wrong, but I remember couple of people have reported issues when burning it on Mac. Yeah, cd burning should be the same, but I'm not 100% the bootloader part is compatible. Although it seems you are booting the cd.

Apart from confirming the ISO is good, do you have an option to burn it on windows or linux?

---

### Post by enigma55 on 2012-05-12
Yeah thanks for the recommendation, I have access to a PC I'm redownloading on now. I'll make sure to MD5 too. I'll let you know how it goes.

---

### Post by enigma55 on 2012-05-12
I just downloaded and burned a new image on a different computer (running windows 7 this time), and it still boots to BusyBox. This time no error is displayed. I tried booting the old DVD again it sometimes displays no error too. I'm thinking something else is wrong.

I tried to do an MD5 on the windos computer, but I don't have admin so I can't install any MD5 program. When I put it in the mac to do the check, it says it can't read the medium and doesn't let me do an MD5

---

### Post by darkod on 2012-05-12
So, you are using the Try Ubuntu to get to live mode and it doesn't go very far, right?

It could be video issue but usually it doesn't show that error for video issues. Are you sure the cd drive of the machine is good?

Try booting the other computer with the same CDs/DVDs. That will give you a clue.

---

### Post by enigma55 on 2012-05-12
I just managed to do an MD5 on the windows, it was good. I tried pressing exit out of the busybox, it told me to type "init=bootarg", and I did, and it gave me another set off erros. I took a picture and am attaching now. 

[IMG]http://i.imgur.com/xhmSw.jpg[/IMG]

---

### Post by enigma55 on 2012-05-12
> **darkod said:**
> So, you are using the Try Ubuntu to get to live mode and it doesn't go very far, right?

It could be video issue but usually it doesn't show that error for video issues. Are you sure the cd drive of the machine is good?

Try booting the other computer with the same CDs/DVDs. That will give you a clue.


I downloaded the full ubuntu x64 iso and I'm using that. I'm pretty certain the cd drive is good, it is external if that makes a difference. I'll try attaching it to another computer and giving it a try.

---

### Post by enigma55 on 2012-05-12
> **enigma55 said:**
> I downloaded the full ubuntu x64 iso and I'm using that. I'm pretty certain the cd drive is good, it is external if that makes a difference. I'll try attaching it to another computer and giving it a try.

I just gave that a try, I attached the exact same external drive to another computer, and it worked perfectly. I'm trying to reformat the HD now

---

### Post by Rubi1200 on 2012-05-12
Good luck and let us know what happens.

---

