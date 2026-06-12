---
title: "Wont boot into gdm - screen flicker's"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by barbz127 on 2009-10-25
Hi all

after testing 9.10 64 bit RC in a VM and the live cd I deceided to take the plunge.

Grub2 has picked up my windows 7 folder which i was worried about but, after the grub menu, then the ubuntu logo on its own I get taken to the console and the screen flickers.

I have logged in, and tried to start gdm manually but I get the flicker and no errors.

I have also tried the good ole "sudo dpkg-reconfigure xserver-xorg" but it doesnt give me the normal menus that im used to, it just goes onto the next line at the console.

Any ideas?

Cheers
Paul

---

### Post by yaztromo on 2009-10-25
Exactly same here. In my case it's probably something nvidia related. I'm going to just try a fresh install and see what happens.

---

### Post by barbz127 on 2009-10-25
im running a nvidia gtx275 -worked fine everywhere previously :(

let me know how you go.

Paul

---

### Post by NRDNick on 2009-10-25
I had some similar issues when I first installed the alpha, luckily all I had to do was reboot the system and gdm loaded fine. I believe I may have booted to a shell a few times by selecting the recovery option in GRUB to run ```
Sudo nvidia-xconfig
``` Of course this only applies if you're using Nvidia drivers.
Hope you get it going

---

### Post by barbz127 on 2009-10-25
> **NRDNick said:**
> I had some similar issues when I first installed the alpha, luckily all I had to do was reboot the system and gdm loaded fine. I believe I may have booted to a shell a few times by selecting the recovery option in GRUB to run ```
Sudo nvidia-xconfig
``` Of course this only applies if you're using Nvidia drivers.
Hope you get it going


Thanks, I cant get into the gdm at all so I cant install the nvidia drivers.

I have tried it in recovery mode and there are no erroes, ive tried to start the service and the "program" (?) /init.d and still no success.

I ran and apt-get upgrade and it didnt make a differnece (just wanted to try).

Im going to reinstall and see if it makes any difference.

Paul

---

### Post by barbz127 on 2009-10-25
a Reinstall has fixed it.

Installing restricted drivers now and we are set.

Cheers
Paul

---

### Post by yaztromo on 2009-10-25
I'm still in trouble. Reinstalled and still the same. Boots and then I see a flickering console login prompt.

Hazarding a guess there's a problem with the open source nvidia driver. Anyone know how I can install the restricted drivers from a recovery console?

---

### Post by yaztromo on 2009-10-25
Fixed it.

If anyone runs into this and you have nvidia hardware do the following:

1. Boot into recovery mode
2. Select console with networking
3. 
```

apt-get install nvidia-glx-185 nvidia-settings
reboot

```

---

