---
title: "Booting from USB using Grub2?"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by syko21 on 2009-10-22
I have a slightly older motherboard that doesn't support booting from fat32 usb (Gigabyte P35-DS3L). It's rather irritating to burn a new cd for each alpha or if I want to test another distro. I was wondering if there was any way to boot a USB from grub2 (it's already installed and functioning) so I could just rewrite it at my leisure and it wouldn't be as laggy as a livecd. Any help is appreciated. Thanks.

---

### Post by kansasnoob on 2009-10-22
Well there's a "how to" here:

[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

but I've not tried it!

Good place to find more info:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by JustRon on 2009-10-22
The tutorial posted above won't help you if your motherboard can't boot from USB. But you can chainload to the USB drive bootloader with the following Grub2 menuentry (replace the "(hd1,1)" part with your USB drive location if necessary):

```

menuentry "Boot from USB drive" {
    set root=(hd1,1)
    chainloader +1
}

```

---

### Post by andrewabc on 2009-10-22
Get cd-rw so you are not wasting cds every time a new release is put out.

Just an idea. :)

I agree that livecd is much slower than liveusb.

---

### Post by drs305 on 2009-10-22
syko21,

Depending on what you want to do, you can just run ISOs from your hard drive now if you wish. Grub 2 will mount and run the Ubuntu LiveCDs without any trouble. Not as great as a VM but it certainly reduces the lag of a CD.

I haven't gotten around to putting it into the post kansasnoob linked, but here is the way to do it:
[Booting LiveCD from HD ISO]("http://ubuntuforums.org/showthread.php?t=1295506")

I only posted this a few days ago so I'm still looking for feedback on user experiences with it.

---

### Post by VMC on 2009-10-23
> **syko21 said:**
> I have a slightly older motherboard that doesn't support booting from fat32 usb (Gigabyte P35-DS3L).
That is a fairly new m/b. I found a couple of things for you. Did you try fat instead of fat32?

Read this [link]("http://forums.anandtech.com/messageview.aspx?catid=29&threadid=2234725"), about several people able to boot thumb drives using that m/b. Read the link to its entirety. I think its the 7th entry that your interested in.

Also this from Gigabyte:
```
Q:When "USB 2.0 controller" is disabled in BIOS, I noticed some USB ports are not available.
 
A:This is chipset limitation. ICH9 embedded two EHCI Host Controllers and six UHCI Host Controllers, supporting up to twelve USB ports.
When USB 2.0 controller is (set) disabled , EHCI #2(EHCI Host Controllers)and UHCI#4 ,UHCI#5 ,UHCI#6(UHCI Host Controllers) are not available.
Therefore, rear USB ports are not available and only front USB ports are available.
```
 
So maybe just a simple BIOS setting. Have you checked your BIOS settings?

---

