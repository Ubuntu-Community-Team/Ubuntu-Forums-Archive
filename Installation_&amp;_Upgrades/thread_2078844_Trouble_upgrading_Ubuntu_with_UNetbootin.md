---
title: "Trouble upgrading Ubuntu with UNetbootin"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by Popenuj on 2012-10-31
Hello,
I'm brand new to Ubuntu and new to this forum. I have a MacBook and my hard drive in it died. I purchased a new one but decided to just install Ubuntu. Since I am a college student away from home, and computers that will let me burn dvds, I installed Ubuntu 9.04 that I got from an Ubuntu user guide. Since I cannot burn a dvd and do not want to spend the money on a usb drive and I cannot find my old one at the moment, I tried to use UNetbootin to install Ubuntu 12.04 from my hard drive. I downloaded the ISO from the Ubuntu site. When I open UNetbootin it says that I don't have 7z or whatever. I tried to download it but I get an error message and am informed it downloaded an alternative version. Either way, I get the error message and then UNetbootin opens anyways. I select to install the ISO using my hard drive and it prompts me to reboot. Here's the problem, when I enter the GRUB and select UNetbootin it immediately pops up and says error 15 file not found. I've searched online but other people have their error 15 message preceded by other messages. Sorry if this narrative was too long but I don't know what is important. Any help would be very much appreciated!

---

### Post by darkod on 2012-10-31
Can't you at least borrow or buy a usb stick? They are very cheap.

I don't think you can install using the hdd as source, at least not in an easy way. Think about it for a moment, you want the hdd to serve as source but at the same time when the installing starts it needs to repartition the same hdd that it's using as a source... I don't see an easy way, and frankly wouldn't bother.
On top of that you want to install on a Mac. I'm not sure how that would work out.

Create the live usb with unetbootin and then use that to boot and install on the hdd.

Which OS are you using to prepare this, another windows computer? unetbootin uses 7-zip to unpack the ISO, that's why it complained about 7z. I know there is 7-zip for windows, never looked for a version for another OS.

---

### Post by Popenuj on 2012-10-31
I bought an unformatted hard drive and installed Ubuntu 9.04 from a disk I had. I'll just give in and buy a USB, this is just costing me a lot of money already. Thanks, I kind of figured I was just being stubborn!

---

### Post by darkod on 2012-10-31
Smart choice. Just a note, if you already have 9.04 running you can use the 12.04 ISO and the Start Up Disk Creator to create the live usb with 12.04. That's the best way, not unetbootin.

After that you can boot with that usb and install 12.04 over the 9.04.

---

### Post by Popenuj on 2012-10-31
Alright, thank you very much!

---

