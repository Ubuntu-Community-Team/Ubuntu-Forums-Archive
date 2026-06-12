---
title: "Wubi installed me Ubuntu for 64bits in my 32bits laptop"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by luismartin on 2013-02-04
I've installed Ubuntu in my laptop today usinbg Wubi. It's an old laptop and it's 32bits. Everything has gone well, except that the intallation of other applications has been too slow. No prompt to choose any version. I've finally installed XAMPP for Linux, and tried to run Apache. That's when I've realized that I have the 64bits version. This is the error message when trying to run Apache (sudo /opt/lampp/lampp start):

**XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.**

What have I done wrong? Is there anything else I could do apart from uninstalling this Ubuntu installation and reinstalling a 32bits version?

---

### Post by TheFu on 2013-02-04
First, your old laptop may support x64 instructions.  You can check this a number of ways, but if the laptop boots with a 64-bit kernel, then your CPU definitely supports amd64 processing commands.
**$ more /proc/cpuinfo**
will show which CPU and CPU extensions are currently available.

The error you are seeing is that the XAMPP is compiled as a 32-bit (no 64-bit version exists in the repositories that your install knows about).  You need to load the 32-bit-to-64-bit compatibility library packages.  That is easy.

$ **sudo apt-get update && sudo apt-get install ia32-libs**
will do it.

If you want to learn more about x32 vs x64, [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit) will explain further.

---

### Post by luismartin on 2013-02-04
Hello TheFu, thanks for your reply.

I've tried to run what you said:
**sudo apt-get update && sudo apt-get install ia32-libs**

The second one gives an error. I'm getting it in Spanish because this is my language but maybe you could help me anyway if I paste it here:

```
sudo apt-get install ia32-libs
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
 ia32-libs : Depende: ia32-libs-multiarch pero no es instalable
E: No se pudieron corregir los problemas, usted ha retenido paquetes rotos.
```

Basically it seems to say that ia32-libs is not installable

---

### Post by bcbc on 2013-02-04
There's a bug for this: ([https://bugs.launchpad.net/wubi/+bug/1093819](https://bugs.launchpad.net/wubi/+bug/1093819))

```
sudo dpkg --add-architecture i386
sudo apt-get update
```

---

### Post by luismartin on 2013-02-05
Perfect! That solved the problem! Thanks a lot!  :KS

BTW, just a question coming up: could I also use a 64bits version of Windows in this laptop? Yes, I know this forum is not for Windows and most of us hate Windows, but I still need both systems, and I'm sure you will answer this question better than in a Windows forum.

Regards!

---

### Post by luismartin on 2013-02-05
Everything is running very slow. Too slow to be a properly configured Linux. Wine is giving me problems too. I can't install any pre-configured app that comes with Winetricks. There are annoying freezes that remind me of Windows. I didn't ever get so many issues when using Linux.

So, I think I'm better going to uninstall Ubuntu and do a fresh install from CD. Wubi completely discarded.

Regards!

---

### Post by TheFu on 2013-02-05
When to run 32-bit or 64-bit OSes is fairly easy to determine, but it depends on 
* CPU
* RAM
* OS
* programs you want to use.
Each of these goes into whether a 32-bit OS or 64-bit OS is better or not.

However, WINE works best on 32-bit Linux, so if your main intention is to run Windows applications under WINE, then staying on 32-bit Linux is most likely the best solution.  However, there are fantastic Linux alternatives to most Windows programs.  I use MS-Windows for 3 programs - everything else runs under Linux.  Those programs are
* Video Editing (VideoRedu Plus)
* Video Recording  (Win7 Media Center)
* Financial Tools (Quicken and Investors Toolkit)
I have gotten Quicken to work under WINE and my instructions are what most people follow.

Another option to WINE is running a virtual MS-Win machine.  This does require a full Windows license, so it does defeat the purpose if saving money is the primary goal. It also required a Core2Duo or better CPU and 2+GB of RAM.  I haven't dual-booted in over a decade, thanks to VMs.  Virtual Machines, VMs, do not work well for Windows gaming, however.  Anything where high-end graphics performance is needed usually does not do well for virtualization.

Anyway, there are many, many articles on the internets about whether to run a 64-bit or 32-bit OS, so let google teach you.

---

### Post by grahammechanical on 2013-02-05
In case anybody is wondering - Ubuntu install DVDs do not have multiple versions of Ubuntu for different CPUs.

We can download either a 64bit version (amd64) or a 32bit version (i386). If Wubi installed 64bit Ubuntu it is because the DVD had a 64bit (amd64) Ubuntu on it.

You can remove that version of Ubuntu from Windows, using Add/Remove programs I guess. You can download the i386 Ubuntu and install that instead. The Ubuntu.com download page for the desktop has the 32bit version as the default (recommended) version.

Regards.

---

### Post by bcbc on 2013-02-05
The 32-bit is only recommended because not all computers are 64-bit and they don't want users to think they should pick it and then find it doesn't work. I've seen discussions on changing the default on the developers discussion list about this and there is a blueprint for it here: [https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-64bit-by-default](https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-64bit-by-default)

To the OP - Wubi runs a bit slower than a normal install, but not that much slower. You might have some hardware that needs a custom driver if you're seeing such problems. (Either that or what you are doing is much slower on Wubi). But it's better to switch to a normal dual boot anyway - so go for it.

---

### Post by luismartin on 2013-02-07
Thanks for all your replies and advices.

The Fu: I only wanted to have Wine because I wanted to try running the Adobe applications on Ubuntu. I haven't figured out how to do it yet, but I tried Inkscape twice and I didn't like the way it works, mainly regarding shortcuts and keys combinations (it sort of reminded me of Corel Draw). Also, because of Spotify. There's a Linux prototype but it gives problems from time to time. For anything else, Linux have everything I need.

grahammechanical: I didn't use any DVD to install from Wubi. I just downloaded it from my laptop, which is 32bit, and it installed a 64bit Linux.

I will definitely remove the Wubi installation and reinstall it from DVD.

Regards.

---

### Post by TheFu on 2013-02-07
> **luismartin said:**
> The Fu: I only wanted to have Wine because I wanted to try running the Adobe applications on Ubuntu. I haven't figured out how to do it yet, but I tried Inkscape twice and I didn't like the way it works, mainly regarding shortcuts and keys combinations (it sort of reminded me of Corel Draw). Also, because of Spotify. There's a Linux prototype but it gives problems from time to time. For anything else, Linux have everything I need.


RANT: Adobe has proven to be a poor friend to F/LOSS. The management of Adobe seems to be negligent towards their client in regards to creating and releasing software that can be used safely.  I am not the only person with this belief:  [https://krebsonsecurity.com/tag/adobe/](https://krebsonsecurity.com/tag/adobe/)

The simple fact is that we should all avoid using Adobe products of any sort unless we make a living from them.  There are alternatives for almost every Adobe tool for non-professionals.  The only Adobe tool that I have not found a reasonable alternative for is Flash, but I am not a pro with most of their other tools besides the PDF ones - which is their worst software from a security perspective, so we need to limit the use to very specific needs and only from highly, highly trusted sources. /RANT

Sorry about that. It needed to be said.

I've never tried inkscape so I don't really know the purpose and when it comes to vector drawing, I admit, a complete addiction to MS-Visio. It helps me make a living.

I am happy that you are dropping WUBI. That is a good thing.  Since you are probably doing high-end graphics stuff, then dual-booting is probably better than running a virtual machine, though it is most definitely less convenient.

If your machine has over 3.5G of RAM, you might want the 64-bit version of Ubuntu if you work with extremely large files.  The 32-bit version can address all the RAM - even more than 4G - now, but it cannot work with data files in certain poorly designed programs that are over 4G in size while in RAM. Does that make sense?  Very, very, very few people will be impacted by this limitation. It is a per-process limitation if I understand it correctly.  

Of course, the 64-bit version of WINE cannot support many 32-bit only Windows programs. That is a known limitation of WINE. Even so, WINE is far from perfect the list of working programs compared to all the programs desired is tiny.

---

