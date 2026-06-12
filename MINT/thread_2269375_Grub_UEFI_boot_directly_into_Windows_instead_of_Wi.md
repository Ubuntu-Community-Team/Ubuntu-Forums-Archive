---
title: "Grub UEFI boot directly into Windows instead of Win bootloader"
date: 2015-03-15
forum: MINT
---

### Post by HierisIngo on 2015-03-15
Hello,

I recently installed Linux Mint 17.1 on my UEFI laptop with already Windows 7 and Windows 8 installed on it. Everything is working fire, except Grub finds and shows the Windows bootloader instead of Windows 7 and Windows 8. This means when I want to boot a Windows OS, I have to pass two bootloaders (Grub and Windows bootloader), which is kinda frustrating. Is there a way to add a startup entry of Windows 7 and one of Windows 8 into Grub that directly boots the WinOS?
(Boot-info report available here: [http://paste2.org/3IPgp4YI](http://paste2.org/3IPgp4YI))

Thanks!

(Sorry for my bad English)

---

### Post by coffeecat on 2015-03-15
You posted to an Ubuntu official flavours section whereas you are running Mint, so I've moved this to the correct section. 

So that people can help you with this, I suggest you run the boot info report that will give all relevant information. You can find that here:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

That should work in Mint if you add the yannbuntu repository. Don't try a repair - just run the report and either post the pastebin url or post the report text if you choose the local report option.

---

### Post by HierisIngo on 2015-03-15
> **coffeecat said:**
> You posted to an Ubuntu official flavours section whereas you are running Mint, so I've moved this to the correct section. 

So that people can help you with this, I suggest you run the boot info report that will give all relevant information. You can find that here:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

That should work in Mint if you add the yannbuntu repository. Don't try a repair - just run the report and either post the pastebin url or post the report text if you choose the local report option.

Thanks for the reply!

Here's the report: [http://paste2.org/3IPgp4YI](http://paste2.org/3IPgp4YI)

---

### Post by ajgreeny on 2015-03-15
I am pretty sure this is the way that two installed versions of MS Windows will have to work.  I'm not sure if this has always been so or if it is a result of the way a UEFI machine boots, as I have never had a dual boot with more than one windows OS, nor dual booted a UEFI machine.

---

### Post by yancek on 2015-03-16
Windows bootloaders are backward compatible and will detect earlier versions of windows only and create entries for both.  This has always been the case as far as I know.  I'm not sure if it matters that you are using UEFI and don't know why you have two efi partitions?  Doubt if that matter though.

---

