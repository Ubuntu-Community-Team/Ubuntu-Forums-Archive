---
title: "Doubts about kernel update"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by -Marco on 2014-12-23
I installed trusty yesterday, all working and having updated everything and installed the drivers open Intel me activated Mesa and various 3D acceleration. 
Then I installed MATE, really fantastic (brings me back to the old days), but finally bored of everything (yes, soon will compile a ROM with my team), I decided to upgrade the kernel with Kernel-Update. 
This, however, installed a kernel without driver Ubuntu, stark, and among other things I miss became the kernel. Immediately uninstall the kernel 3.18


 Then with Synaptic I saw it was available, by Canonical (Ubuntu or officially) the 3.13.0-44 that was finally provided with the driver and then ufficialissimo. Install, ok (but I also install other parts of the kernel that the old non HAD, extra-type image, image-build etc.) And there it is installed. Reboot and find myself always the damn 3.13.0-43 and the new not in use. Vane research to use the new kernel .. :( I uninstall the kernel again and back to square one.
 I went of Synaptic and says that my kernel no longer update (that is, as if it had never left the 44-xxx) POSSIBLE? I'm coming out crazy ahaha. The official repo says that I've no one update but I have only installed the 43-xxx installing trusty beginning. Jesus. 
Just think Utopic say that is going to have the 3:18

---

### Post by Bucky Ball on 2014-12-23
```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Try that in a terminal and please post back the full output of any errors between [code] tags.

---

### Post by -Marco on 2014-12-23
> **Bucky Ball said:**
> ```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Try that in a terminal and please post back the full output of any errors between ```
 tags.
There are no error. No update available. All pack are up-to-date..
Final output (i'm italian, but it says no update for packs):
[code]Lettura elenco dei pacchetti... Fattokillmhz@PCdiMarco:~$ sudo apt-get upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Calcolo dell'aggiornamento... Eseguito
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
killmhz@PCdiMarco:~$ sudo apt-get dist-upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Calcolo dell'aggiornamento... Eseguito
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
```

---

### Post by schragge on 2014-12-23
First, let's find out what kernel are you currently running. Run the following command in terminal
```

uname -r

```
and post the output here.

Next, let's see what kernels are installed on your system, and which of them are present in the boot menu. Please post the output of the following commands
```

ls /boot/vmlinuz*
awk '/^kernel/{print $2}' /boot/grub/menu.lst

```

BTW, to get the output in English, prefix your commands with *LC_ALL=C* like
```

LC_ALL=C sudo apt-get upgrade

```

---

### Post by -Marco on 2014-12-23
> **schragge said:**
> First, let's find out what kernel are you currently running. Run the following command in terminal
```

uname -r

```
and post the output here.

Next, let's see what kernels are installed on your system, and which of them are present in the boot menu. Please post the output of the following commands
```

ls /boot/vmlinuz*
awk '/^kernel/{print $2}' /boot/grub/menu.lst

```
uname -r says:
```
3.13.0-43-generic
```
The other one say:
```
killmhz@PCdiMarco:~$ ls /boot/vmlinuz*/boot/vmlinuz-3.13.0-43-generic
killmhz@PCdiMarco:~$ awk '/^kernel/{print $2}' /boot/grub/menu.lst
awk: cannot open /boot/grub/menu.lst (No such file or directory)
```

So I have the **3.13.0-43** and I knew it. 
P.S: Awk command doesn't work, if you see that :(

---

### Post by schragge on 2014-12-23
Ah sorry, my fault, that should have been
```
awk '$1=="linux"{print $2}' /boot/grub/grub.cfg
```
but this is needless now as you seem to have only one kernel installed

---

### Post by -Marco on 2014-12-23
> **schragge said:**
> Ah sorry, my fault, that should have been
```
awk '$1=="linux"{print $2}' /boot/grub/grub.cfg
```
but this is needless now as you seem to have only one kernel installed
Display this:
```
killmhz@PCdiMarco:~$ awk '$1=="linux"{print $2}' /boot/grub/grub.cfg/boot/vmlinuz-3.13.0-43-generic
/boot/vmlinuz-3.13.0-43-generic
/boot/vmlinuz-3.13.0-43-generic
```
Yep, I've one kernel and i wanna update it. How can I get the last official kernel for trusty? (not utopic) :)
P.S: This kernel it's good for me, but i'll develop on Xperia Z3 and in this kernel i don't found any driver et similae. For this i want to update it ;)

---

### Post by schragge on 2014-12-23
3.13.0-43 is also the latest default kernel for trusty as you can see [here]("http://packages.ubuntu.com/trusty/linux-generic"). To get 3.13.0-44 you should enable the pre-released updates repository (**trusty-proposed**).
In Synaptic, open **Settings > Repositories** (or **Impostazioni > Archivi dei pacchetti**), third tab there is **Updates** (or **Aggiornamenti**) and check the **trusty-proposed** repository.

---

### Post by Bucky Ball on 2014-12-23
> **schragge said:**
> 3.13.0-43 is also the latest default kernel for trusty ...[/B]).

Why do you need a newer kernel which isn't meant for Trusty at this point? Either way, you can get the .deb files from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/") and follow the instructions [here]("http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/"). It is really only a matter of a couple of clicks once you have the .deb files locally.

You can find .debs for 3.18 quite easily also if you want to go there. You don't need PPAs.

Sound like Trusty will be going to 3.16 for 14.04.2 in any case. Good luck. ;)

---

### Post by schragge on 2014-12-23
Well, the 3.16 kernel is also packaged for trusty. If that is what you want, just install the package **linux-generic-lts-utopic**.

---

### Post by -Marco on 2014-12-23
> **Bucky Ball said:**
> Why do you need a newer kernel which isn't meant for Trusty at this point? Either way, you can get the .deb files from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/") and follow the instructions [here]("http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/"). It is really only a matter of a couple of clicks once you have the .deb files locally.

You can find .debs for 3.18 quite easily also if you want to go there. You don't need PPAs.

Sound like Trusty will be going to 3.16 for 14.04.2 in any case. Good luck. ;)
Oh good, i hope that it'll come in January or in 2012Q1 before April, so 15.04!
Yes, it's strange, but i can't develope a driver for my Xperia Z3. I must use my old netbook with Lubuntu 14.10 for the last kernel.. but.. it's got a single core celeron (2003) and my home PC got an i5-4670K. The differences between this device are big.

> **schragge said:**
> Well, the 3.16 kernel is also packaged for trusty. If that is what you want, just install the package **linux-generic-lts-utopic**.
Dude, I've installed x.y.z-44 and it hasn't any drivers (from mice to wifi). I remove it and now i keep x-43.
It's normal? In this case if i'll install 3.16, do it work flawless or i get same problem as x-44?

---

### Post by Bucky Ball on 2014-12-23
> **-Marco said:**
> 
... if i'll install 3.16, do it work flawless or i get same problem as x-44?

Only one way to find out. ;)

We can't really tell you as that would require one of us having exactly the same hardware and config you have. That would be unlikely.

---

### Post by -Marco on 2014-12-23
> **Bucky Ball said:**
> Only one way to find out. ;)

We can't really tell you as that would require one of us having exactly the same hardware and config you have. That would be unlikely.
Gotcha, you're right. I'll test soon :)

---

### Post by -Marco on 2014-12-23
Last problem. With Windows 8.1 i play, for example, L4D2 to 1080p at MAX Detail (+ VSync ecc.) 60fps smoothness
Now with Ubuntu+Open Intel Driver (o I01) i run at unstable 40-50fps at 900p with mid-high detail.
Does Linux kernel run faster than windows kernel? so for what reason i play worst? :(

---

### Post by schragge on 2014-12-23
Are you sure what you need is a newer kernel, and not a newer Xorg video driver for your graphics card, for example?

---

### Post by -Marco on 2014-12-23
> **schragge said:**
> Are you sure what you need is a newer kernel, and not a newer Xorg video driver for your graphics card, for example?
No, for the moment I'm using this kernel. No problem for me.
Xorg driver is up-to-date (i've installed the 01Linux Intel Driver updated to December) and this one installed all the PPAs for next update. There aren't any update now.

Xorg driver, anyway, don't change the situation. I run L4D2 and other game on 2013 with these driver and looks the same as now. Only Borderlands 2 got more 5fps.
:(

---

