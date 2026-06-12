---
title: "Installing Ubu 19.04 - Lenovo 110s-11IBR, boot super slow."
date: 2019-07-21
forum: Installation &amp; Upgrades
---

### Post by viralthread on 2019-07-21
Over the weekend I picked up a Lenovo 110s-11IBR in excellent condition, obviously it had Win10 preinstalled. It also has a 32GB eMMC installed so it has 2x32GB internal space onboard. 

As per usual with my notebooks, I booted the machine to a USB Stick I made using Rufus and the latest install image available. 

The machine does boot into Ubuntu, but the process takes several minutes.

Originally I thought this might be related to booting from the USB, only the USB 2 slot seemed to allow booting properly, but once installed, the system still takes an excruciating amount of time to reach a logon prompt. 

I am using the default Rufus settings, and have not made adjustments for GPT or anything. I disabled secure boot in the BIOS and toggled off the 'optimise for operating systems' switch but none of these seems to resolve the issue. 

I reinstalled Windows 10 from a clean stick and it works flawlessly, boots in under 15 seconds from a cold start. 

So the big question is, what am I doing wrong? I have several laptops that have Ubuntu or some flavor thereof (Lubuntu is a favorite of mine) and all of them behave in the same fashion, as well as a Parrot OS live boot and a Kali live boot. 

Am at a loss, suggestions welcome. 

Thanks in advance.

---

### Post by viralthread on 2019-07-21
Update - 

Opened the machine, removed the eMMC and rebooted, installed Lubuntu. 

Install goes ok, machine takes 60s from time encryption password is entered to initialize the boot process, which seems to go speedily after. 

Any suggestions? 

I am not comfortable running a machine without encryption.

---

### Post by &amp;wP*!) on 2019-07-22
Type following commands and copy-paste here their outputs. That will ease the universe to help you faster: 
```
lsblk -D -f -l
sudo lshw -C memory
systemd-analyze blame
```

---

### Post by viralthread on 2019-07-22
Thank you for the advice. Alas the machine has ceased to boot for reasons unknown, I'm just getting a dead LCD. 

Obviously not as excellent as I thought. 

Relegated to the shelf for now until I have time to tear it down.

---

### Post by viralthread on 2019-07-24
Ok, so to wrap this up so I don't leave it hanging, here's a summary of what I did to get this little badboy up and running. 

I tore the machine down to the last screw, cleaned everything, reseated the cooling pad with some fresh artic silver, and reassembled the machine. 

Updated the machines BIOS to the most current one, and replaced the realtek wireless card that was pre-installed with one I ripped from a Dell I had sitting around with a bad SD Card reader (Same SOC and form factor). 

Machine now boots in about 45-60s (probably a bit draggy due to encryption), and once it's up and running she purrs like a kitten. 

Wireless throughput is solid, machine seems stable, few hiccups streaming NetFlix now and then, overall performance more than acceptable for total investment of <$50.

---

