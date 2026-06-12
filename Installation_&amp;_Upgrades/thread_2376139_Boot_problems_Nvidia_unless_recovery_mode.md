---
title: "Boot problems Nvidia unless recovery mode"
date: 2017-10-30
forum: Installation &amp; Upgrades
---

### Post by holleke on 2017-10-30
Dear ubuntu lovers

Since I'm using ubuntu on my new pc with intel and gtx970 I keep having problems booting.

When i am booting in the default way I get this weird screen ([https://i.imgur.com/RShzJ0G.jpg](https://i.imgur.com/RShzJ0G.jpg)) but when I'm not using my GPU (so just on motherboard) or in recovery mode everything works fine.

Are there more people with this problem ? Or someone with a solution ?


Thanks for considering my request.

---

### Post by ajgreeny on 2017-10-30
Try booting with the **nomodeset** boot option which may get you to a low resolution GUI from which you can use "Additional Drivers" to install the appropriate nvidia driver for your GTX970.

---

### Post by holleke on 2017-10-30
Had already tried that but didn't work :/

---

### Post by SeijiSensei on 2017-10-30
First, run the command "lsmod".  Do you have an entry like this:

```
nvidia              13008896  224 nvidia_modeset
```

If so, try running "sudo nvidia-xconfig" then rebooting.

If not, you're not using the proprietary driver.

---

### Post by holleke on 2017-10-31
So I found the problem I had but Monodeset and not Nomodeset in the /etc/default/grub.
Big Thanks :)

---

### Post by ajgreeny on 2017-10-31
The word should be all in lower case, ie nomodeset, not Nomodeset.

However, great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

