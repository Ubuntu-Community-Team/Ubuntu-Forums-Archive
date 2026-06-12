---
title: "New PC build but Linux will not boot correctly"
date: 2021-01-07
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2021-01-07
Hello I just finished a new computer build it's a Ryzen 5, 3600, I tried booting a USB of Ubuntu mate but nothing will boot, I even tried booting Ubuntu mate from a SSD I have installed on this machine

I have two hard drives installed in this machine. I did install a hard drive with Windows 10, and everything seems to work ok. Could it be something in my BIO that's stopping Ubuntu mate from booting. The mother board I have is a Aorus B450 Pro Wifi if this will help

Thanks so much

---

### Post by ActionParsnip on 2021-01-07
Have you tried a different USB port (One attached to the motherboard)? 
Did you set the BIOS to boot USB first?
Does the BIOS show the USB stick when you navigate within setup?
Does the Ubuntu USB stick boot in other systems?
Did you MD5 test the ISO you downloaded?

---

### Post by RobGoss on 2021-01-07
Yes I did just about everything you mentioned but still can't get Ubuntu to boot correctly. The usb I used works fine in my other machines. I'm thinking maybe the bios needs flashing but Windows runs fine not sure what it is. Ubuntu will boot at one point but them it just hangs at the boot screen 

Thanks

---

### Post by mIk3_08 on 2021-01-07
[Click here]("https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview"), [Here]("https://help.ubuntu.com/community/Boot-Repair") & [Here]("https://ubuntuforums.org/showthread.php?t=2147295") it might help your needs.

---

### Post by TheFu on 2021-01-07
There are a number of BIOS changes needed to boot non-MSFT operating systems.  Read the manual and there is a "ubuntu uefi" guide that google finds easily with other tips.

---

### Post by ubfan1 on 2021-01-07
Definitetly check for firmware updates, for both the motherboard and SSD.  Try the latest kernel, 20.10, or even the daily build of 2104.

---

### Post by oldfred on 2021-01-07
Often UEFI and if SSD, SSD firmware updates are required. You may need them even if new system.
Possible similar issues:
Gigabyte B450 Ryzen needs updated kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247) & 
[https://ubuntuforums.org/showthread.php?t=2423649](https://ubuntuforums.org/showthread.php?t=2423649)

---

### Post by mIk3_08 on 2021-01-08
try usb 2.0 port not on 3.0 ports as it always looks for its driver when using it maybe it will help.

---

### Post by TheFu on 2021-01-08
With Ryzen, there are a few needed things that Intel CPUs didn't usually need.
Always flash the MB firmware, especially when using a Ryzen 3K on a B4xx motherboard. There are many reasons for this, but mainly compatibility with newer parts.
Depending on the RAM used, you may need to check the speed.  I've had to slow down by 3200Mhz RAM to 2800 Mhz to get a stable system. The XMP (D.O.H.C.) RAM settings weren't stable. Also had to relax two of the main RAM settings and verify that the voltage was slightly higher. With 2 sticks, it wasn't this hard, but when I filled all 4 RAM slots, it became more picky.

There are multiple settings that are for Windows and UEFI. Those are recommended to be disabled. Read the motherboard manual.  I have no idea how someone is supposed to dual boot without using 2 different BIOS profiles. Fortunately, many current motherboards support having 4 different BIOS hardware profiles, but I don't know about your specific MB or BIOS.

I spent a few hours searching motherboard tweaking sights to find all the settings. Unfortunately, most will be for OC and gamers on Windows.

---

### Post by RobGoss on 2021-01-08
> **TheFu said:**
> With Ryzen, there are a few needed things that Intel CPUs didn't usually need.
Always flash the MB firmware, especially when using a Ryzen 3K on a B4xx motherboard. There are many reasons for this, but mainly compatibility with newer parts.
Depending on the RAM used, you may need to check the speed.  I've had to slow down by 3200Mhz RAM to 2800 Mhz to get a stable system. The XMP (D.O.H.C.) RAM settings weren't stable. Also had to relax two of the main RAM settings and verify that the voltage was slightly higher. With 2 sticks, it wasn't this hard, but when I filled all 4 RAM slots, it became more picky.

There are multiple settings that are for Windows and UEFI. Those are recommended to be disabled. Read the motherboard manual.  I have no idea how someone is supposed to dual boot without using 2 different BIOS profiles. Fortunately, many current motherboards support having 4 different BIOS hardware profiles, but I don't know about your specific MB or BIOS.

I spent a few hours searching motherboard tweaking sights to find all the settings. Unfortunately, most will be for OC and gamers on Windows.

This is my second Ryzen build the first one runs just fine I can boot Linux and Windows with  out having to update the BIOS, I thinking it 's just this motherboard that might need tweaking, oh and by the way the motherboards are the same in brand but this last one has much more features

I am currently running BIOS 51, and when I did a bit of searching I believe 61, is available at the moment....

---

### Post by RobGoss on 2021-01-08
> **oldfred said:**
> Often UEFI and if SSD, SSD firmware updates are required. You may need them even if new system.
Possible similar issues:
Gigabyte B450 Ryzen needs updated kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247) & 
[https://ubuntuforums.org/showthread.php?t=2423649](https://ubuntuforums.org/showthread.php?t=2423649)

Hello Fred thanks so much for the helpful information my friend

---

### Post by RobGoss on 2021-01-08
Thanks so much everyone I will take your suggestions and do a bit more research

---

### Post by kurt18947 on 2021-01-10
I agree with the others, upgrade the BIOS unless it's pretty recent. I generally don't load the latest unless it's been out for a while, I flash 1 version old. If there are problems with that one, the problem is more likely to be known. I had an Asrock AB350M board that required a certain BIOS version to boot 2nd or 3rd generation Ryzen CPUs. I currently have an MSI B450 board that worked out of the box.

---

### Post by RobGoss on 2021-01-10
> **kurt18947 said:**
> I agree with the others, upgrade the BIOS unless it's pretty recent. I generally don't load the latest unless it's been out for a while, I flash 1 version old. If there are problems with that one, the problem is more likely to be known. I had an Asrock AB350M board that required a certain BIOS version to boot 2nd or 3rd generation Ryzen CPUs. I currently have an MSI B450 board that worked out of the box.

Thank you Kurt, the problem I'm having is no matter what I try I cannot update the BIOS I have 51 bios version and it's showing there's another version 61 available. But when I try using the flashing feature within the BIOS it always fails

I have Windows 10 installed on one drive but wanted to install Ubuntu mate on a new 500 GB SSD with no luck

---

### Post by ubfan1 on 2021-01-10
Take a look at [https://www.gigabyte.com/Motherboard/B450-AORUS-PRO-rev-10/support#support-dl-bios](https://www.gigabyte.com/Motherboard/B450-AORUS-PRO-rev-10/support#support-dl-bios) -- some of the older entries like F40's suggestion to use a new flash tool:  EC FW Update Tool (B19.0517.1 or later version) to avoid 4DIMM DDR incompatibility on 3rd Gen AMD Ryzen&#8482; CPU.  Might try a different flash mechanism.  Another thought I had, does the W10 use bitlocker?  BIOS/firmware changes might invalidate the TPM key, and ask your for a "recovery key"  -- which if you never set one up, and never had one squirreled away on the sly when you set up a Microsoft Account or domain account, you would be out of luck, until maybe a factory reset gets you back to something the TPM recognizes.  Anyway, might be better/necessary to turn off bitlocker before a flash, then turn it back on.  The link stops at 60e, so maybe another site would be better to examine for release notes on your 61.

---

### Post by RobGoss on 2021-01-10
> **ubfan1 said:**
> Take a look at [https://www.gigabyte.com/Motherboard/B450-AORUS-PRO-rev-10/support#support-dl-bios](https://www.gigabyte.com/Motherboard/B450-AORUS-PRO-rev-10/support#support-dl-bios) -- some of the older entries like F40's suggestion to use a new flash tool:  EC FW Update Tool (B19.0517.1 or later version) to avoid 4DIMM DDR incompatibility on 3rd Gen AMD Ryzen&#8482; CPU.  Might try a different flash mechanism.  Another thought I had, does the W10 use bitlocker?  BIOS/firmware changes might invalidate the TPM key, and ask your for a "recovery key"  -- which if you never set one up, and never had one squirreled away on the sly when you set up a Microsoft Account or domain account, you would be out of luck, until maybe a factory reset gets you back to something the TPM recognizes.  Anyway, might be better/necessary to turn off bitlocker before a flash, then turn it back on.  The link stops at 60e, so maybe another site would be better to examine for release notes on your 61.

> Another thought I had, does the W10 use bitlocker? BIOS

I'm not really sure I would have to look into that, I'm assuming **bitlocker** would in the BIOS some were correct?

thanks so much

---

### Post by #&amp;thj^% on 2021-01-10
I set one of these up once for customer to boot both Win10 And Linux, he was very additament about not touching anything with **Secure Boot** to install. (I wanted to just let him keep his PC and take it elsewhere) But I accepted the challenge. I did not disable Secure Boot on this install.
BitLocker Device Encryption is enabled by default since Windows 8.1 **_if it has the proper hardware and the user signs in with a Microsoft Account_**, and Windows 10 expanded on that. 

Depending on your device, you may have to boot into your installation usb/media from the Windows Settings app: System and Updates: Recovery: Advanced Startup. (That makes sense right?)

For new readers here, ***You shouldn’t select to use the entire drive.*** I_f you want to Keep Windows._...Wiser choice would be to dual boot Windows/Linux or use a another drive for your install.

---

### Post by ubfan1 on 2021-01-10
Excuse the rant, but Bitlocker may be a time bomb waiting to brick your machine. New machines (W10 pro) come with encrypted disks and Bitlocker inactive. (Huh? read the below).

Bitlocker is Microsoft's commercial product for key management -- not the key that encrypts your data/disk (Full Volume Encryption Key, FVEK), or even the
key (Volume Master Key, VMK) which encrypts the FVEK, but keys to encrypt the VMK.  Lots of keys to provide some mechanism to respond to a user who asks 
for help getting their data back, after losing their recovery password....  These key storage/generation mechanisms are numerous and not all under user control.  You can avoid some 
of these mechanisms, but not all.  By not setting up the network on a new machine, no Microsoft Account can be generated (so no copy of a recovery key can be made).
Likewise not joining a domain.  The Tusted Platform Module (TPM) can generate a key (to decrypt the VMK) using certain hashes of platform values (PCR registers)
(like BIOS hashes, etc.) so just copying the disk and trying to read it on another machine will fail.

The gotcha:  New machine come with the disk already encrypted!  Bitlocker "activation" is just setting up a few more recovery mechanisms. If you never
"activate", you are still running an encrypted disk, relying on the TPM and certain hashes to decrypt -- note, no password, or pin necessary for this
mechanism.  Everything may be fine for months, until maybe a Windows update or a BIOS update or device order change occurs and the TPM hashes decide the machine is different
and not to be trusted, so asks for another mechanism: "Please enter the "recovery" key. Oh my, that key may never have been set up.  There may be no other mechanism to decode the VMK.
 If you're lucky, you can reverse whatever change occured, and recover your data.

The lesson:  If you leave the (Bitlocker) disk encryption in place, at least generate a recovery key for your own use.

 If you turn off the encryption (manager-bde -off /dev/sdxy) what have you lost?
Your disk/data may be copied.  Your device (laptop) may be stolen and data exposed.

If you think it's necessary to really protect something valuable, you should at least
consider the following questions:
1)Who generated the FVEK? Microsoft, the vendor, the government,... who knows.
2)Is the FVEK in some database along with the MAC addr, CPU ID, device serial no.?
3)How many copied of the database exist, who has access? 
4)How easy is to to make a new database copy --  court order, employee bribe,...?

It would appear the security horse has left the barn, before you set up your first
recovery key. Setting up a Microsoft Account and storing a Bitlocker recovery
key there, may not make things much worse.  

For those who take responsibility for safeguarding/storing keys they generate themselves,
there are other mechanisms for disk encryption.

---

### Post by RobGoss on 2021-01-11
>    BitLocker Device Encryption is enabled by default      


Is this something I have to disable in my BIOS?

---

### Post by ubfan1 on 2021-01-11
You can see the status of your Bitlocker situation with
manage-bde -status
Somewhat misleading, since Protection off just means you haven't set up any of your recovery keys.  Look at the disk encryption label, it's 0% when decrypted.
To decrypt the disk, use
manage-bde -off
My new SSD only took about 10 minutes to finish,.
There was nothing in my UEFISettings/BIOS that I changed, but I suppose any TPM settings would change things -- mabe not for the better.  If your TPM has your only "recovery" key, and you clear it, you have just bricked your machine.  Figure out first if you want disk encryption, and either turn it off or make another recovery key of your own.  Relying only on the TPM's PCR hashes for decoding will lead to much grief (Google has many such cases).

---

### Post by RobGoss on 2021-01-11
> **1fallen said:**
> I set one of these up once for customer to boot both Win10 And Linux, he was very additament about not touching anything with **Secure Boot** to install. (I wanted to just let him keep his PC and take it elsewhere) But I accepted the challenge. I did not disable Secure Boot on this install.
BitLocker Device Encryption is enabled by default since Windows 8.1 **_if it has the proper hardware and the user signs in with a Microsoft Account_**, and Windows 10 expanded on that. 

Depending on your device, you may have to boot into your installation usb/media from the Windows Settings app: System and Updates: Recovery: Advanced Startup. (That makes sense right?)

For new readers here, ***You shouldn’t select to use the entire drive.*** I_f you want to Keep Windows._...Wiser choice would be to dual boot Windows/Linux or use a another drive for your install.

Thanks so much, this is a stand alone build and I will not be dual booting, every OS will have it's own SSD....

This setup has become troublesome not having any luck flashing the BIOS and cannot get any tech support for Gigabyte

---

### Post by #&amp;thj^% on 2021-01-11
> **RobGoss said:**
> 
This setup has become troublesome not having any luck flashing the BIOS and cannot get any tech support for Gigabyte
Sorry to hear that. :(
Wouldn't they have a Bios CD they could send...or are they just not replying?
Come to think about it>>>New Mother board>> should have come with a CD for Bios.

---

### Post by ubfan1 on 2021-01-11
The gigabyte site   [https://www.gigabyte.com/us/Motherboard/B450-AORUS-PRO-rev-10/support#support-dl-bios](https://www.gigabyte.com/us/Motherboard/B450-AORUS-PRO-rev-10/support#support-dl-bios) only offers the BIOS F60e as the latest (12/09/2020), not the F61 you mentioned.  Try the F60e to update the F51.  Where did you get the F61 version?  I know my new Dell came with a firmware rev. beyond what's offered on the web site, but F51 is definitely at least one rev back.

---

### Post by RobGoss on 2021-01-11
> **1fallen said:**
> Sorry to hear that. :(
Wouldn't they have a Bios CD they could send...or are they just not replying?
Come to think about it>>>New Mother board>> should have come with a CD for Bios.

I have a CD the board came with but I don't have a CD drive in this machine only USB ports

Maybe I could get a External CD Drive and install it that way. I'm not sure what's on this CD would they have BIOS update on it?

I looked at the CD it says drivers utilities

---

### Post by RobGoss on 2021-01-11
> **ubfan1 said:**
> The gigabyte site   [https://www.gigabyte.com/us/Motherboard/B450-AORUS-PRO-rev-10/support#support-dl-bios](https://www.gigabyte.com/us/Motherboard/B450-AORUS-PRO-rev-10/support#support-dl-bios) only offers the BIOS F60e as the latest (12/09/2020), not the F61 you mentioned.  Try the F60e to update the F51.  Where did you get the F61 version?  I know my new Dell came with a firmware rev. beyond what's offered on the web site, but F51 is definitely at least one rev back.

Sorry my mistake I meant bios 60e, I've tried downloading the 60e and unable to flash it...

---

### Post by CelticWarrior on 2021-01-11
> **RobGoss said:**
> Sorry my mistake I meant bios 60e, I've tried downloading the 60e and unable to flash it...

Would you mind sharing exactly how are you trying to do that?

---

### Post by RobGoss on 2021-01-12
> **CelticWarrior said:**
> Would you mind sharing exactly how are you trying to do that?

Sure, I downloaded the latest bios files 60e, extracted it plugged my USB in copying those extracted files to that USB

I then when into my bios and used the Q flash option chose the bios files but I always get a error can't flash this file

---

### Post by oldfred on 2021-01-12
What format is USB?
UEFI only reads from FAT32.

I made my ESP larger & changed permissions so I could use it and my downloaded UEFI updates go into ESP. And then read direct from UEFI the file I downloaded.

---

### Post by RobGoss on 2021-01-12
> **oldfred said:**
> What format is USB?
UEFI only reads from FAT32.

I made my ESP larger & changed permissions so I could use it and my downloaded UEFI updates go into ESP. And then read direct from UEFI the file I downloaded.

I believe its FAT.32, Fred

I'm assuming my BIOS need to set to UEFI correct?

---

### Post by oldfred on 2021-01-12
There is not really BIOS anymore, its CSM. For UEFI update no setting should be required.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

And CSM is extra chip and software to do that emulation. UEFI class 3 is UEFI without CSM.

Intel is planning to end "legacy BIOS" support in their new platforms by 2020 in requiring UEFI Class 3 or higher.
[http://www.uefi.org/sites/default/files/resources/Brian_Richardson_Intel_Final.pdf](http://www.uefi.org/sites/default/files/resources/Brian_Richardson_Intel_Final.pdf)
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

---

### Post by RobGoss on 2021-01-12
I don't see secure boot, only fast boot

---

### Post by oldfred on 2021-01-12
Some systems call Secure boot as "Windows" or "Other".
My older system said if installing Windows 7 you have to use "Other". Windows 7 did not support Secure Boot, so that was the UEFI Secure boot setting.

---

### Post by RobGoss on 2021-01-16
Just a quick update, I managed to install the latest versions of Manjaro and PopOS, on this same machine and all went well so I'm assuming there's something wrong with the Ubuntu's distro's like Mate,and Ubuntu, that stopping the installations

Could it be a driver issue?

---

### Post by RobGoss on 2021-01-19
bump

---

