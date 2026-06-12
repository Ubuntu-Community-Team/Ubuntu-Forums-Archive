---
title: "[SOLVED] Broadcom wireless BCM4328 not working in Intrepid"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by HDave on 2008-10-26
I have been using ndiswrapper with Gutsy and Hardy with success.  After an upgrade to Intrepid a few days ago, my wlan0 interface no longer appears in network manager or within "ifconfig".  However the hardware device still appears if I do "lshw -C network".

I uninstalled everything that was associated with ndiswrapper, hoping to get jockey to correctly apply the correct driver.  Jockey shows me two wireless drivers (both appeared in the dialog following the upgrade) -- "wl" and "Broadcom B43 Wireless Driver".  Neither one works and I have no idea why.

I am really looking forward to using native Linux drivers, so any help here is much appreciated!

---

### Post by Ayuthia on 2008-10-26
> **HDave said:**
> I have been using ndiswrapper with Gutsy and Hardy with success.  After an upgrade to Intrepid a few days ago, my wlan0 interface no longer appears in network manager or within "ifconfig".  However the hardware device still appears if I do "lshw -C network".

I uninstalled everything that was associated with ndiswrapper, hoping to get jockey to correctly apply the correct driver.  Jockey shows me two wireless drivers (both appeared in the dialog following the upgrade) -- "wl" and "Broadcom B43 Wireless Driver".  Neither one works and I have no idea why.

I am really looking forward to using native Linux drivers, so any help here is much appreciated!

If they both show up, try using the wl driver.  I don't think that the b43 supports your card at this time.  Once you have it enabled, go to the Terminal and try the following (will only work for the current session):
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```
If it works, then you are not blacklisting something.

---

### Post by eternal_sage on 2008-10-26
i am also having this exact same problem. this is a fresh intrepid install (wiped my wife's laptop last night and installed the release candidate) and i'm getting the exact same problems as the OP, complete with the wl, broadcom proprietary drivers thing.

have not checked the above suggestion, as i'm getting the XP partition working right now, will try in a bit.

oh, and btw, i also disabled the broadcom driver, and the wl driver said it was enabled but not active. is this just a symptom of a greater problem, or maybe the problem itself?

---

### Post by eternal_sage on 2008-10-26
i ran the above commands and got the following

```
courtney@Cortana:~$ sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
FATAL: Module ssb is in use.
courtney@Cortana:~$ sudo modprobe wl
courtney@Cortana:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
courtney@Cortana:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

courtney@Cortana:~$ 

```

---

### Post by superm1 on 2008-10-26
It sounds like you might have another driver using the b44 driver.  Try to rmmod b44 and try all those steps again.

---

### Post by Ayuthia on 2008-10-26
> **eternal_sage said:**
> i ran the above commands and got the following

```
courtney@Cortana:~$ sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
FATAL: Module ssb is in use.
courtney@Cortana:~$ sudo modprobe wl
courtney@Cortana:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
courtney@Cortana:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

courtney@Cortana:~$ 

```

I agree with superm1.  It does look like b44 is loaded because of the ssb message.  Please try again with the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
```

If it does work, please the results of lspci -nn and if you really need the b44 module, I can give you a script to add so that it will load the b44 module after the wl driver is loaded.

---

### Post by HDave on 2008-10-26
I too got the message "FATAL: Module ssb is in use.".

So I went ahead and did the "rmmod b44".  This allowed modprobe to remove the ssb module.  After this I could get my wireless working just fine.

The problem is, it was my ethernet adapter that was using this "b44" module.  (What is this b44 module anyway?)

Any idea how I can get both to work at the same time without ndiswrapper?

---

### Post by Ayuthia on 2008-10-26
Sorry, I was confused when I saw eternal_sage's post.  eternal_sage has another one in an ndiswrapper post.  My post should have read:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```

If that works, you can create the following script:
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```

EDIT:
> The problem is, it was my ethernet adapter that was using this "b44" module. (What is this b44 module anyway?)
The b44 module (driver) is what makes your ethernet adapter work.  The driver requires the ssb module (Sonic Silicon Backplane) which is something that is inside of Broadcom cards.  However, if the ssb module finds a device that it needs (like the wireless and wired cards for your computer), it will not share with other drivers.  So if you need it to work, you have to load it after the module that you need (in this case, the wl module).  Hope that makes sense.

---

### Post by HDave on 2008-10-26
Ayuthia -- Thank you very much.  All is now well.

Am I to understand that the ssb kernel module is a driver that, once loaded, will only talk to the other modules already loaded.

In other words, there is a loading dependency where wl, and b44 need to be loaded first and then ssb?

If so, is this a defect I should report to launchpad or can we all expect it to be addressed before 8.10 release?

---

### Post by Ayuthia on 2008-10-26
> **HDave said:**
> Ayuthia -- Thank you very much.  All is now well.

Am I to understand that the ssb kernel module is a driver that, once loaded, will only talk to the other modules already loaded.

In other words, there is a loading dependency where wl, and b44 need to be loaded first and then ssb?

If so, is this a defect I should report to launchpad or can we all expect it to be addressed before 8.10 release?
ssb is actually called by the b44 module.  The b44 module needs the ssb module so it will load it automatically.  The problem occurs because the b44 module is built into the kernel module where the wl module is not.  So when the system boots up, it will load the b44 module first.  Then it will load all the other non-builtin modules afterwards (like the wl module).  Since the b44 module is loaded, the ssb is loaded also.  Then the wl module will try to load, but will not be able to attach to the wireless device because the ssb module already found it.  That is why the workaround is needed.

So, I am not really for sure about how to call this issue.  I would guess that someone has already posted one in launchpad, but you can check.

---

### Post by HDave on 2008-10-26
> **Ayuthia said:**
> So, I am not really for sure about how to call this issue.  I would guess that someone has already posted one in launchpad, but you can check.

After some searching I located [this]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/263097") bug report on which I have added my two cents.  Thanks again.

---

### Post by eternal_sage on 2008-10-27
ahh thank you! that version worked well!

one rather newbish question though. how do i make that script work? never done what i'm guessing is a bash script, although i've heard of them. thanks a ton!

---

### Post by Ayuthia on 2008-10-27
> **eternal_sage said:**
> ahh thank you! that version worked well!

one rather newbish question though. how do i make that script work? never done what i'm guessing is a bash script, although i've heard of them. thanks a ton!

The script automatically runs when the module is loaded.  All you have to do is copy the command and paste it in the Terminal:

wl (Broadcom STA):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
echo wl | sudo tee -a /etc/modules
```

ndiswrapper:
```
echo -e '#ssb workaround, added `date`\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
echo ndiswrapper | sudo tee -a /etc/modules
```

I added an extra command to have the system load the wl/ndiswrapper module.  ndiswrapper needs it so that the system knows to load it after it loads the kernel module.  I think that the wl module might need it also.

---

### Post by eternal_sage on 2008-10-27
ok. forgive my density here, but just wanting to make sure i totally understand what going on before i start mucking about in the console. all i need to do is copy the above script (which ever one i need) into the console this one time, and it will then work automatically for her on out, without the need to run those commands each time? thanks again.

---

### Post by HDave on 2008-10-27
> **eternal_sage said:**
> ok. forgive my density here, but just wanting to make sure i totally understand what going on before i start mucking about in the console. all i need to do is copy the above script (which ever one i need) into the console this one time, and it will then work automatically for her on out, without the need to run those commands each time? thanks again.

Yes.

---

### Post by eternal_sage on 2008-10-28
ok, that script apparently didn't work for some reason. i pasted it into the console and hit enter, it did its thing, and then on restart i still had to run the modprobe commands to get it working again.

to boot, something has thrown off the card in MY laptop (which has been working in intrepid since mid august out of the box). i just discovered this problem a few moments ago and haven't had time to investigate (since its worked perfectly for the last 2 versions of ubuntu without me touching it, i can't remember what the card type is off hand).

edit: ok, after digging around, i've found that i have a BCM4401 in this beast. is it possible to be a similar bug as the previous?

edit2: ok, it seems not, as no permutation of the above (that i could formulate at least) helped me. maybe because i'm doing something wrong, as i only kind of understand the problem to begin with.

---

