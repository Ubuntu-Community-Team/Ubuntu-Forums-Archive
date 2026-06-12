---
title: "Upgrade from 20.x to 22.x broke, system won't boot (VirtualBox issue?)"
date: 2023-05-17
forum: Installation &amp; Upgrades
---

### Post by cyberminion on 2023-05-17
Hello,

I've been running Ubuntu 20.04 LTS for a while. It kept wanting to upgrade, so I finally did. It ran me through the upgrade wizard, downloading and installing the new OS, replacing FF with the FF snap, migrating user data, updating the grub config, etc. Then it rebooted. My bootloader was fine, and I booted into Ubuntu. However, it brought me to an Ubuntu splash screen I have not seen before, and just sat there. No HID support, no user input options. I let it set for over 24 hours, just in case it was trying to do...something...but no, it was stuck. Rebooting to Ubuntu brought me to the same place, same result. I let it sit for hours more, but still nothing. Subsequent reboot attempts just show the realtime initialization log output, with the last entry being: 
"[FAILED] Failed to start LSB: VirtualBox Linux kernel module"

I did have VirtualBox installed on v20. Is this causing the boot sequence to break somehow, post-upgrade? Any ideas how I might fix this?

Thank you!

---

### Post by MAFoElffen on 2023-05-17
The full error for that is:
```

[FAILED] Failed to start LSB: VirtualBox Linux kernel module.
See 'systemctl status virtualbox.service' for details.

```
Please post he output of 
```

sudo systemctl status virtualbox.service | grep .

```

---

### Post by MAFoElffen on 2023-05-17
Sorry. Meanwhile, back at the ranch... Then I noticed your title, where it says "it won't boot."

Boot to the Grub Menu. Choose Advanced > Select a Rescue option. Select enable Networking. Then select Root shell...

Step one
```

modprobe vboxdrv

```
Reboot and test. If that didn't work, then back to rescue mode root prompt

Step 2
```

/etc/init.d/vboxdrv setup

```
Reboot and test. If that didn't work, then back to rescue mode root prompt

Step 3
```

apt install --reinstall virtualbox

```
Reboot and test.

---

### Post by cyberminion on 2023-05-18
Okay, I'll try those now. While waiting, I may have broken things more...

I noticed that I can boot with kernel v5.15.0-71 (presumably the old version I was running), so I did that, and removed VirtualBox via apt. On boot to the new kernel version (5.19.0-41), it now just tells me sector count, then clears the screen, and hangs, with the text cursor's blink even stopping. Then I tried recovery mode on kernel 5.19, and ran autoremove to see what that would suggest. It prompted to remove vboxnetadp.ko and vboxnetflt.ko . What the heck, it's already broken, right? I told it to do that. The result was the same as before the autoremove. No more Virtualbox error, just sector count, clear screen, then frozen text cursor.

Update: The first two returned errors, since it no longer knows what virtualbox is (my fault). Enable networking isn't working...still no network connectivity when I do that, so apt can't get anything. I'll keep working on that.

---

### Post by cyberminion on 2023-05-18
At first I thought it was a networking issue, but no, it is working. However, after telling me how large the install will be...

[It breaks.

also it can't seem to access any third party repos, but that is probably just how it works in this environment.

Any ideas?

Thank you!!

---

### Post by MAFoElffen on 2023-05-18
Try this first:
```

ping -c 4 www.google.com
ping -c 4 8.8.8.8

```

---

### Post by cyberminion on 2023-05-18
Well.

Okay, you're right. I was wrong that I was wrong about the network connection working. Nothing.

Just to verify, I did the same on a different OS using the same hardware and network connection. That worked fine.

So Ubuntu's rescue environment isn't connecting to the network. Now what?

Should I just be overwriting this mess with a fresh OS, rather than spending hundreds of hours troubleshooting?




EDIT: The network connection also works when I boot to Ubuntu's rescue environment under the older kernel, v5.15.0-71. What would happen if I use apt to reinstall Virtualbox under that kernel version?

---

### Post by MAFoElffen on 2023-05-18
```

root@Ub-APH3:~#

```
Is that from the Rescue Mode "Root Prompt"? If so, then type "exit"... To get back to the Rescue Menu > Select "Enable Networking"... Then go back to the "Root Prompt" and try again.

I put that in my instructions above, but you night not have seen that...

---

### Post by cyberminion on 2023-05-18
Yes. I actually did see, and do, that. 

Upon entering the rescue environment, I first select the "enable networking" option. Some output flashes on the screen too quickly for me to read, then it clears, and brings me back to the recovery environment menu. I then select "root prompt" and do these tests. This process did work when using the old kernel version. However, I still couldn't ping out on the new kernel version's rescue environment.

---

### Post by MAFoElffen on 2023-05-18
So, does that mean with the older kernel, you could run and ping out?

---

### Post by cyberminion on 2023-05-19
Correct. It works with the older kernel, just not the new one.

---

### Post by ajgreeny on 2023-05-19
I've moved the thread to Virtualisation as it is a better fit.

I have Vbox 7 on my system so will try updating my VM to the same kernel you are having trouble with to see if there may be a kernel incompatibility with my version of VBox.
Which VBox version are you using?

---

### Post by cyberminion on 2023-05-19
Hi,

I think I was running VBox 6.1.38. I installed the repo's latest stable version in April, 2023. It has now been uninstalled, but perhaps the damage to the new kernel is already done?

I don't believe I even built any VMs on this system. Just installed it, planning to use it in the future.

---

### Post by ajgreeny on 2023-05-19
*Thread moved back to **Installation & Upgrades**.* which is more appropriate and a better fit.
My apologies for the first move; I thought the OS in question was a VM running in VBox, but that was incorrect I now believe.

---

### Post by cyberminion on 2023-05-19
Correct, the Ubuntu upgrade in question was running natively. The only reason VirtualBox entered into the discussion was that when the host OS tried to boot (immediately after the upgrade), it was showing an error related to VirtualBox just before the procedure would hang.


At this point, should I just be installing a fresh 22.x OS over this wrecked install?

---

### Post by ajgreeny on 2023-05-21
Having scanned back through this thread it seems possible that your version of VBox is incompatible with the new kernel version that you have moved to.

Before a total reinstall of your system i suggest you purge the current install of VBox to totally get rid of everything, then install VBox version 7 from the VBox website at [https://download.virtualbox.org/virtualbox/7.0.8/virtualbox-7.0_7.0.8-156879~Ubuntu~jammy_amd64.deb](https://download.virtualbox.org/virtualbox/7.0.8/virtualbox-7.0_7.0.8-156879~Ubuntu~jammy_amd64.deb) and install that. All your VMs will remain in your home wherever you put them and should run in the new version 7 without a problem.

I don't use VBox very much now having moved almost entirely to KVM/QEMU but the one VM I do use it for runs excellently with no problems at all, and has never shown a problem with my kernels, of which I have both the 5.15 and 5.19 series available.

---

### Post by cyberminion on 2023-05-21
So I did previously uninstall it via the recovery environment under the new kernel version. However, the new kernel's recovery environment can't connect to the network, so I can't install it through there. 

I did just try reinstalling it under the old kernel's recovery environment. It installed successfully, but the upgraded system still can't boot. I just get to see that that VirtualBox error once again, just prior to the boot process hanging, as it always has.

As I reminder, I can also still boot into the OS GUI under the old kernel version, too.

---

