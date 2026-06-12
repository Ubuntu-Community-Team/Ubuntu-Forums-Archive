---
title: "ubuntu will not load or install."
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by Sgnob on 2012-11-03
I recently bought a new laptop from Walmart.  [http://www.walmart.com/ip/Toshiba-Satin-Black-Trax-15.6-C855D-S5315-Laptop-PC-with-AMD-Dual-Core-E-300-Accelerated-Processor-and-Windows-8-Operating-System/21684639](http://www.walmart.com/ip/Toshiba-Satin-Black-Trax-15.6-C855D-S5315-Laptop-PC-with-AMD-Dual-Core-E-300-Accelerated-Processor-and-Windows-8-Operating-System/21684639)  and I can get ubuntu 12.4, 12.10, or Linux mint 13. to run on it. Iv tried both 32 and 64bit. versions. Iv tried to boot from disk and usb drive. When I try to run try before installing it just goes to a blank screen and hangs. Same thing if i try to install. Iv also tried to install via wubi and it dose install but crashes on boot and gives me a MS screen saying to put in a windows recovery disk. Iv also removed the hard disk drive thinking it may be a problem with Windows 8 and just running from disk and the same thing, Just a hangs with a blank screen. Any ideas? If its a hardware problem I need to know so I can return it. I vary rarely use windows and ubuntu is my OS of choice.

Thanks in advance
Sgnob

---

### Post by ibjsb4 on 2012-11-03
I do not own a Toshiba, but been looking around and seems to me its the AMD Radeon HD 6310.

Take a look at these links.

[https://help.ubuntu.com/community/RadeonDriver#Unsupported](https://help.ubuntu.com/community/RadeonDriver#Unsupported)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=AMD+Radeon+HD+6310+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=AMD+Radeon+HD+6310+&as_qdr=all&sa=Google+Search&lang=en)

Anyhow thats my best guess.

---

### Post by Sgnob on 2012-11-03
Thanks for the reply,, Im going back to Wallyworld to look at some other laptops. From what I remember most of them have Radon graphics.. I look to see if I can find one a little more Linux friendly. Thanks for the input, I had a feeling it was a graphics issue. Its been a while since I've been around a computer.

---

### Post by Bashing-om on 2012-11-03
HI ! Sgnob;

Another thought, as this is a "new" computer, is UEFI booting; Requiring ubuntu install to match windows booting mode.

 How is Windows booting, in BIOS mode or in EFI mode? You can find out by typing "bcdedit" in a Windows Administrator Command Prompt window and looking for the "path" line in the "Windows Boot Loader" section. If this line refers to winload.efi, then you're booted in EFI mode; if it refers to winload.exe, then you've booted in BIOS mode.

Though the "black screen is certainly indicative of a graphics driver issue.

When you attempt to boot the install disk, do you get as far as the screen with the stick figure and keyboard emblems ?
if so -> escape->language screen->escape->boot options screen-> try the f6 option-> choose "nomodeset", f10 to continue to boot.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by Sgnob on 2012-11-03
OK, its in EFI mode.. And after I select try or install all I get is a blank screen. I'm going to do some searching about EFI now and see what options I have. Thanks.
Edit
So I went into my BIOS and took it out of UEFI mode, and booted up ubuntu :) and selected try before installing. Posting this from my ubuntu trial season now.. many thanks. Now I need to make some windows recovery disks, just in case I decide to return this laptop. And I see how it installs. I will post any video issues if I have any.

---

### Post by ibjsb4 on 2012-11-03
Nice call bashing

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=UEFI+mode&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=UEFI+mode&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Sgnob on 2012-11-03
So is there any benefit to being in UEFI mode? I really don't use windows but there are times I need Active x controls to remote view my security cameras. So I was thinking of dual booting with Windows 8 which this computer came with.. So I guess my question is how hard is it going to be to install Ubuntu on a different partition. I really do not like how wubi installs it inside windows and would like to stick to the old faction way im used to doing it. I'm reading up on installing in EUFI mode but its been a while and it looks might it may be a long night as Iv haven't used an computer in a while and my old lap top was 10years old running 10.4 which I loved.
Thanks for the help guys!!

Edit..
pulling my hair out here.. For the life of me I cant get 12.10 64bit to load in UEFI mode.. Is there something im missing?

Edit.... So I was not able to get 12.10 amd64 to boot in UEFI mode. :(  I did a lot of reading and I wasn&#8217;t able to find a working solution, so I just installed it in legacy and using it now, its a little buggy but that expected seeing that I may have some hardware issues. WiFi is not working correctly and my video is not supported well. Any way thanks for the help.

---

