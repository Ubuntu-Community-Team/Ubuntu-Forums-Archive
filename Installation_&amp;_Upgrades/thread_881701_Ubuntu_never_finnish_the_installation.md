---
title: "Ubuntu never finnish the installation"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by megauser on 2008-08-06
Hello,
I tried to install Ubuntu on an old crappy computer ~500mhz, IDE HDD and so on. It now has Win 2000 installed on it. I want a fresh copy of Ubuntu on it, no dual boot.

So first I tried the "demo version" when you can check it out. It boots up and you can see the "chicken wallpaper" but nothing happens after that. You can see the mouse pointer and all but it lags like hell and nothing happens. The window to proceed the installation never pops up.

Exactly same thing happens when you choose to install instead of trying it out.

Tried multiple times and leaved it on for 4h. Even checked the CD if it was OK.

I got no Linux experience really.

---

### Post by iaculallad on 2008-08-06
What is the amount of your system RAM?

---

### Post by snowpine on 2008-08-06
Sounds to me like your system doesn't have enough ram (384mb required)--I would suggest checking out Xubuntu, which is a version of Ubuntu that works better on older computers (only 192mb required for the normal installation). Good luck!

---

### Post by megauser on 2008-08-06
Hey thanks for the fast answers. I am not sure of the amount of RAM in the computer. It is not my computer but I doubt its that much. Will give xubuntu a try.

---

### Post by snowpine on 2008-08-06
When you first boot up the computer, there's a key you can press (it's F2 for me) to enter the bios. That will show you how much ram you have.

Here are some rough minimum ram requirements for the different ubuntu derivatives:

384 Ubuntu
256 Ubuntu alternate CD
192 Xubuntu
128 Xubuntu alternate CD
64 Fluxbuntu

Note that performance may be slow if you only have the minimum. Better to choose something with a little extra, for example, Xubuntu is really nice with 256mb of ram.

---

### Post by megauser on 2008-08-07
It has 130 in RAM. I decided to give Fluxbuntu a try. It boots up like normal, I choose to install but I nothing really happeneds after the selection is made. It is just a black background with the text.

[ 0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine

Same thing happens when I choose the option to check the CD. Could it be wrong on the CD?

Fast reply appreciated since I am over an working on it now.

---

### Post by snowpine on 2008-08-07
> **megauser said:**
> It has 130 in RAM. I decided to give Fluxbuntu a try. It boots up like normal, I choose to install but I nothing really happeneds after the selection is made. It is just a black background with the text.

[ 0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine

Same thing happens when I choose the option to check the CD. Could it be wrong on the CD?

Fast reply appreciated since I am over an working on it now.

I think I can help with this in a couple of hours when I get home. There should be a way to edit the kernel boot line (perhaps pressing "F6 for more options"?) and turn off ACPI. Probably something like adding "acpi=off" to that line. I'm sorry I don't have my Fluxbuntu in front of me right now. :(

---

### Post by megauser on 2008-08-07
I gave a far shot with Xubuntu even though I doubted it but I saw the exact same message display after I choosed to install it. The different thing was that after a couple of seconds it went on the the installation. Flexbuntu never did. Anyway, it could not be continued when it was inside later. Window never appeard.

---

### Post by snowpine on 2008-08-07
Boot up the Fluxbuntu CD. 
Press F6
Add 'acpi=off' (without the quotes) to the boot options line and delete 'quiet' so you'll get more detailed messages on screen.
Press Enter... let us know what happens!

---

### Post by megauser on 2008-08-21
> **snowpine said:**
> Boot up the Fluxbuntu CD. 
Press F6
Add 'acpi=off' (without the quotes) to the boot options line and delete 'quiet' so you'll get more detailed messages on screen.
Press Enter... let us know what happens!

It worked, Thanks! :guitar:

---

### Post by megauser on 2008-08-21
> **megauser said:**
> It worked, Thanks! :guitar:

False alarm, it did finnish the installation but it wount boot up to the actual OS. I get the same error message again.

[ 0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine

But this time I have no place to type in "ACPI=OFF". :confused:

Edit:
I tryed putting in the CD again and typed in ACPI=OFF and boot from first harddrive. Problem still remains.

---

### Post by snowpine on 2008-08-21
> **megauser said:**
> False alarm, it did finnish the installation but it wount boot up to the actual OS. I get the same error message again.

[ 0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine

But this time I have no place to type in "ACPI=OFF". :confused:

No worries! You can add acpi=off at the GRUB screen.

Now, it will get pretty annoying doing this every time. Once you are logged in, you can edit a file called /boot/grub/menu.lst so that it does it automatically every time. 

Here are detailed instructions:

Restart and press esc for Grub options.
Press 'e' to edit the first Ubuntu 8.04 kernel
Scroll down to the second line that starts with 'kernel' and press 'e'.
Add 'acpi=off' to the end of this line.
Press Enter.
Press 'b' to boot.

Once logged in, open a terminal and:
    gksu gedit /boot/grub/menu.lst

Scroll down and find the same kernel line that you edited in Grub. Add 'acpi=off' here and save the file.

---

### Post by megauser on 2008-08-21
> **snowpine said:**
> No worries! You can add acpi=off at the GRUB screen.

Now, it will get pretty annoying doing this every time. Once you are logged in, you can edit a file called /boot/grub/menu.lst so that it does it automatically every time. 

Here are detailed instructions:

Restart and press esc for Grub options.
Press 'e' to edit the first Ubuntu 8.04 kernel
Scroll down to the second line that starts with 'kernel' and press 'e'.
Add 'acpi=off' to the end of this line.
Press Enter.
Press 'b' to boot.

Once logged in, open a terminal and:
    gksu gedit /boot/grub/menu.lst

Scroll down and find the same kernel line that you edited in Grub. Add 'acpi=off' here and save the file.

Ah so I was almost there myself, I was there and edited myself right now but there is a funny problem.

I can't do the "=" sign. I have a Swedish keyboard and the keymapping is English. I pretty much did Shift+something and can't find it.

---

### Post by snowpine on 2008-08-21
> **megauser said:**
> Ah so I was almost there myself, I was there and edited myself right now but there is a funny problem.

I can't do the "=" sign. I have a Swedish keyboard and the keymapping is English. I pretty much did Shift+something and can't find it.

Wow, never come across that problem myself! Good luck. :)
Maybe start a new thread if you can't figure it out. Ubuntu has a huge international community.

---

### Post by megauser on 2008-08-21
I just did. So silly really, can find most signs but not the "=". We have tried every combo that exist so there must be some sort of workaround.

---

