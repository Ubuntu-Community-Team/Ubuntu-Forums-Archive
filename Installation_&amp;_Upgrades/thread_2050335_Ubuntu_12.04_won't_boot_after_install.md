---
title: "Ubuntu 12.04 won't boot after install"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by Skele on 2012-08-30
I upgraded from Natty to 12.04. The installation process had a lot of errors with libraries. That they won't work after the installation. After it finished the computer didn't restart itself it just was stuck on my desktop. I restarted it myself from the desktop. It went perfectly until it started to boot itself. GRUB shows it failed "Starting Openoffice.org service for Secveri docvert-converter" and the last lines 
"Since the script you are attempting to invoke has been converted to an apstart job, you may also use the start(8) utility, eg. start S90binfmt-support
apache2: Syntax error on line 204 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: libdb-5.1.so: cannot open shared object file: No such file or directory
Action 'start' failed.
The Apache error log may have more information.
* Starting web server apache2  [fail]
* Checking battery state...   [ OK ]
...fail!
*ALSA is not active, cannot start TiMidity++ ALSA midi emulation".
It also says there are "unknown keys" and "invalid rules" at the start and that there are "unknown jobs" like "S90binfmt-support" and "S50cups". After a while copying all this data from the screen it goes blank, propably sleep mode.

I really don't have any clue what to do at this point. Has anyone got any clues on how I can upgrade to 12.04 without losing every drop of information I have on the computer or even if I can upgrade to 12.04?

---

### Post by black veils on 2012-08-30
i cannot answer your direct question. you should already have a backup of your data.. but if not, you can boot live media to choose the Try option, and open the file manager to copy your files to a usb flash drive.

---

### Post by darkod on 2012-08-30
Does the 12.04 cd work fine in live mode?

Can you select to boot the recovery mode in the grub menu instead of the normal mode?

---

### Post by Skele on 2012-08-30
> **black veils said:**
> i cannot answer your direct question. you should already have a backup of your data.. but if not, you can boot live media to choose the Try option, and open the file manager to copy your files to a usb flash drive.

I thought of that same option right after posting this. I'll try it.

---

### Post by Skele on 2012-08-30
> **darkod said:**
> Does the 12.04 cd work fine in live mode?

Can you select to boot the recovery mode in the grub menu instead of the normal mode?

I don't have a cd version of it yet. I upgraded straight from the update management.

No, GRUB doesn't let you choose any options.

---

### Post by darkod on 2012-08-31
> **Skele said:**
> I don't have a cd version of it yet. I upgraded straight from the update management.

No, GRUB doesn't let you choose any options.

Well, next time make a cd first and try it in live mode. That can show you if there are any possible issues with your hardware. If there are, most probably they will be there after the upgrade too.

You mean no grub menu shows up? If you have only ubuntu, the grub menu doesn't show by default (because there is only one OS). After the POST is finished, hold Shift and that will show the menu. But be careful to select the right moment, just after POST finishes and before it actually starts to load ubuntu. Once it starts to load it, it's too late.
If the menu shows, select the recovery mode, then in the menu that shows select first Network, and then Drop to root shell.
If that loads correctly you can try some fixes. First see if it loads.

---

### Post by Skele on 2012-08-31
I tried it with the Live dvd and it works but I can't copy some of the files because I don't have permission. How do I get permission?

---

### Post by darkod on 2012-08-31
You have to be careful when copying, if you want the files to keep their permissions. It's better to do it in terminal as opposed to the Nautilus file browser.

In terminal, you can use sudo to copy as root user with maximum permissions, but for the copied files to keep their permissions you need to use something like cp -ax. So, it would be:
```
sudo cp -ax /source /destination
```

Otherwise, to open Nautilus as root in terminal type:
```
gksu nautilus
```

But in this case I am not sure the copied files keep their permissions. Because if it copies them as root owner, no user will be able to open them later.

If you want to, you can try few basic things before trying to copy, because it might repair the system. Did you try booting the recovery mode from the grub menu?

---

### Post by Skele on 2012-09-02
> **darkod said:**
> You have to be careful when copying, if you want the files to keep their permissions. It's better to do it in terminal as opposed to the Nautilus file browser.

In terminal, you can use sudo to copy as root user with maximum permissions, but for the copied files to keep their permissions you need to use something like cp -ax. So, it would be:
```
sudo cp -ax /source /destination
```

Otherwise, to open Nautilus as root in terminal type:
```
gksu nautilus
```

But in this case I am not sure the copied files keep their permissions. Because if it copies them as root owner, no user will be able to open them later.

If you want to, you can try few basic things before trying to copy, because it might repair the system. Did you try booting the recovery mode from the grub menu?

It worked. After that I just formatted the drive and it works great. Thanks.

---

