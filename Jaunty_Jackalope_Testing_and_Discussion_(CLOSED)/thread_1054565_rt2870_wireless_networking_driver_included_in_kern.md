---
title: "rt2870 wireless networking driver included in kernels after 2.6.28-4?"
date: 2009-01-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by deruberhanyok on 2009-01-29
Hello,

I've a Linksys WUSB600N USB wifi-n network adapter. It uses a ralink rt2870 chipset.

On previous releases up to and including Alpha 3, I was able to get the device working by adding the device ID to the driver source code provided by ralink, making sure WPA supplicant support was enabled for networkmanager, and compiling a kernel module. I was used to doing this every time a kernel update came around.

Well I installed Alpha 3, got the adapter working, went online and downloaded the available updates. This got me to kernel 2.6.28-5 and the driver no longer works. I can make the source code changes, run make, make install and then if I "modprobe rt2870sta" it appears to load the module but doesn't detect the device.

It was pointed out to me that an rt2870 driver appears to exist in staging. If this is going to be implemented permanently that is fantastic, and I just want to know where to file the report to get the device ID added so it works in later releases.

However if something else may be causing the compiled driver to no longer work, I'd appreciate any suggestions about it. I'm about to reinstall Alpha 3 so I can get back online and try the 2.6.28-6 kernel that is now in the repos, but if indeed it is trying to load the included module rather than the one I compile I expect I'll have the same problem with that.

---

### Post by autocrosser on 2009-01-29
The compiled driver will conflict with the included driver in the kernel--I have not compiled anything & have the driver working correctly....make sure you have linux-firmware 1.5 installed & remove every trace of the compiled driver--I only use the /etc/Wireless/RT2860STA/RT2860STA.dat file to configure the driver (using a Encore PCI card with the 2860 chipset).

I can send you my .dat file for you to look at if you want. If the kernel driver won't work, you need to file a bug with the firmware & kernel packages---but make sure you have ALL the old compiled driver stuff removed first---You might consider doing a fresh install to test & hook up wired until you have all the updates in.

---

### Post by deruberhanyok on 2009-01-30
I'll see if the firmware package is installed.

The fresh install is no problem, I was planning on doing that anyways. I'm not sure what would be involved in removing everything I've compiled... I'll look in to that.

Was the driver included in 2.6.28-4? If it isn't there, I'd have to compile the driver to get online to grab the updates... if it was just added in -5 I'd probably have to wait for Alpha 4 to make sure I can try to use the included one without having to compile anything.

I'll post back here once I've played around with it a bit tonight. Thanks for the info, autocrosser.

---

### Post by RaZoR1394 on 2009-01-30
> **deruberhanyok said:**
> I'll see if the firmware package is installed.

The fresh install is no problem, I was planning on doing that anyways. I'm not sure what would be involved in removing everything I've compiled... I'll look in to that.

Was the driver included in 2.6.28-4? If it isn't there, I'd have to compile the driver to get online to grab the updates... if it was just added in -5 I'd probably have to wait for Alpha 4 to make sure I can try to use the included one without having to compile anything.

I'll post back here once I've played around with it a bit tonight. Thanks for the info, autocrosser.

Get in the source dir you used and do:


sudo ifconfig ra0 down
sudo modprobe -r rt2870sta
sudo make uninstall
sudo make clean

I'm not entirely sure if that would work fully but I think it could be worth a try. I'm using the rt2870 as well and would really like to try the Ubuntu drivers.

---

### Post by deruberhanyok on 2009-01-30
Sweet, thanks Razor. I'll report back here with any luck I might have.

---

### Post by deruberhanyok on 2009-01-30
Well I think I got it fully removed but no luck getting the included module to work. I checked and the firmware package is definitely installed.

It looks like the module isn't included in alpha 3 with 2.6.28-4 so I am going to reinstall, compile the driver and try the latest updates. If it doesn't work with those I'll file a bug report. Do you guys think that the USB device ID is all they would need?

---

### Post by deruberhanyok on 2009-01-30
No luck with the clean install and updating to 2.6.28-6. I've filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323473)

Hopefully that will make it in before final. :)

---

### Post by autocrosser on 2009-01-31
Bummer--I know that the 2860 driver works well--sorry to hear that the 2870 driver is not at the same state...Keep on top of your bug report & I'd bet that it gets some attention soon....

---

### Post by Lucretius on 2009-01-31
I've had a hell of a job trying to get wireless working with different chipsets on jaunty...

I have put the blame on network manager as they all seem to work fine with WICD...

try installing it and see if it fixes your problem..

---

### Post by RaZoR1394 on 2009-01-31
Ok? I just tried one of my rt2870 adapters on a laptop with a clean Jaunty installation and it works fine. The light turns on at boot, networks are visible.

I'm currently using the other adapter on my desktop and after the removal procedure I posted it still works fine after reboot.

---

### Post by deruberhanyok on 2009-01-31
I think the 2870 driver is fine, but this particular adapter has a device ID it doesn't recognize without adding it to Ralink's source code.

My guess is that the device ID just needs to be added to the module included with the newer kernels... hopefully there will be a response to the bug report letting me know if the solution is indeed that straightforward.

I also e-mailed Ralink to see if they could add the device ID to the source code, so perhaps in the future the device will work without any alterations to the code required.

---

### Post by autocrosser on 2009-02-25
What adapters are you using? I'm getting an Edimax EW-7718Un that uses the rt2870 chipset & was wondering......

---

### Post by excogitation on 2009-04-04
Should WPA/WPA2 work with a standard Jaunty daily or UNR daily with a rt2860 card?

(Because on my Wind U100 unencrypted works, but not WPA/WPA2)

---

