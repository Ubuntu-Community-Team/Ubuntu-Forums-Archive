---
title: "Ubuntu with snapdragon"
date: 2021-08-21
forum: Installation &amp; Upgrades
---

### Post by telegiovi on 2021-08-21
Dears, I have a new laptop which runs with a processor Snapdragon (TM) 850 @2.96 GHz. I would like to install Ubuntu on it as I always do on my pc's .  Please let me know which ISO image is 
correct to download for my laptop. Thank you!

---

### Post by mikewhatever on 2021-08-21
ISO images are only available for Intel/AMD based hardware. I doubt there is an official Ubuntu option, but search to make sure.

---

### Post by telegiovi on 2021-08-21
Yes there is an ISO for ARM, but for "server". Can I use it on a laptop?

---

### Post by mikewhatever on 2021-08-21
You can try to use it, but I am not sure how well it will work. Unless there is a custom made image for that specific machine, you'll need to do all the heavy lifting. So, good luck, and let us know how it went.

---

### Post by telegiovi on 2021-08-21
I tried. But there is an unexpected problem; bios doesn't let me choose the option of booting others than "original" ; see attached

---

### Post by mikewhatever on 2021-08-21
Well, as said above, start the heavy lifting and figure out how to boot it. 
ARM hardware is different, as you don't just boot from a generic image and install. 
Perhaps there is a way to hook into whatever Windows uses to boot.
I'd try to save time and search if there is anything linux related available for that particular computer model.

---

### Post by tea for one on 2021-08-21
Some years ago, I'm sure that I read various articles about Microsoft locking down the Secure Boot on **ARM** devices.

I can only find this info at the moment (there must be more):-
> ARM computers complying with the requirements must additionally:

    [COLOR="#FF0000"]NOT allow a physically present person to disable Secure Boot[/COLOR]
    NOT allow a physically present person to enable Custom Mode, and modify the list of keys the firmware trusts

Yes. You read that correctly. The Microsoft certification requirements, for x86 machines, explicitly require implementers to give a physically present user complete control over Secure Boot - turn it off, or completely control the list of keys it trusts. Another important note here is that while the certification requirements state that the out-of-the-box list of trusted keys must include Microsoft's key, they don't say, for e.g., that it must not include any other keys. The requirements explicitly and intentionally allow for the system to ship with any number of other trusted keys, too.

These requirements aren't present entirely out of the goodness of Microsoft's heart, or anything - they're present in large part because other people explained to Microsoft that if they weren't present, it'd have a hell of a lawsuit on its hands2 - but they are present. Anyone who actually understands UEFI and Secure Boot cannot possibly read the requirements any other way, they are extremely clear and unambiguous. They both clearly intend to and succeed in ensuring the owner of a certified system has complete control over Secure Boot.

If you have an x86 system that claims to be Windows certified but does not allow you to disable Secure Boot, it is in direct violation of the certification requirements, and you should certainly complain very loudly to someone. If a lot of these systems exist then we clearly have a problem and it might be time for that giant lawsuit, but so far I'm not aware of this being the case. All the x86-based, Windows-certified systems I've seen have had the 'disable Secure Boot' option in their firmwares.

[COLOR="#FF0000"]Now, for ARM machines, the requirements are significantly more evil: they state exactly the opposite[/COLOR], that it must not be possible to disable Secure Boot and it must not be possible for the system owner to change the trusted keys. This is bad and wrong. It makes Microsoft-certified ARM systems into a closed shop. But it's worth noting it's no more bad or wrong than most other major ARM platforms. Apple locks down the bootloader on all iDevices, and most Android devices also ship with locked bootloaders.

[COLOR="#FF0000"]If you're planning to buy a Microsoft-certified ARM device, be aware of this, and be aware that you will not be in control of what you can boot on it.[/COLOR] If you don't like this, don't buy one. But also don't buy an iDevice, or an Android device with a locked bootloader (you can buy Android devices with unlocked or unlockable bootloaders, still, but you have to do your research).

As far as x86 devices go, though, right now, Microsoft's certification requirements actually explicitly protect your right to determine what can boot on your system. This is good.

I added the red font to highlight the important part.

Original text here [https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

---

### Post by MAFoElffen on 2021-08-21
I have Ubuntu Arm Experience... Yes, Ubuntu Server ARM and Ubuntu Desktop ARM (there is both available, not just Server) at or after 20.04 should install... That's what I do. With SnapDragon, that should be AARM64...

ARM does require UEFI and SecureBoot on. At 20.04, being able to boot with SecureBoot is default for all versions. That just means that the newer Kernels are digitally signed as being trusted. 

I install, then install a desktop. Depending to the specific hardware, you may have to find some the specific drivers for quark hardware if they are not there, but most are.

So yes, there are still "some" caveats... but what you mentioned is their already. If you can boot the 20.04 and run the Ubuntu Desktop ARM LiveCD, then it should be fine.

Here's some links for you:
[https://cdimage.ubuntu.com/focal/daily-live/current/](https://cdimage.ubuntu.com/focal/daily-live/current/)
[https://cdimage.ubuntu.com/releases/20.04.2/release/](https://cdimage.ubuntu.com/releases/20.04.2/release/)

---

### Post by tea for one on 2021-08-21
@MAFoElffen

Did your ARM devices have Windows 8 or Windows 10 pre-installed?

---

### Post by telegiovi on 2021-08-22
Preinstalled is Win 10.    Thank you all for your help. At this point I don't know how to go on (by myself).  I'll try to get help from the local Linux group

---

### Post by MAFoElffen on 2021-08-23
Yes and no... AARM64 requires UEFI (big period) and still generally tends to be configured default as  SafeBoot, even if it isn't Windows. This is in machines that are not even supported by Windows. That is a big difference from X86_amd64... I can run Ubuntu 20.04 LTS and newer as either SafeBoot on or off in AARM64.

---

