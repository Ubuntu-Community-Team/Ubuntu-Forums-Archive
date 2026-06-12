---
title: "issues with usb drives - space and input/output errors"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by cpu2007 on 2013-05-11
I never had this problem with w7 but for some reason ubuntu keeps prompting these errors.

Sometime when my usb is full, correctly it states that it cannot copy more data as is full; however if I delete all the content and there's enough space, it still throws the same error saying that there's no space when actually there is.
It also throws an input/output error when trying to copy something.

How can I solve this irritating issue?

Thank you

---

### Post by ibjsb4 on 2013-05-12
Have you checked for a hidden trash folder?

Open it (USB) in Nautilus and **Ctrl + h** to show hidden files.

---

### Post by cpu2007 on 2013-05-12
yes I did, that one has all the files inside as well, is it there anyway to not get that folder when deleting files?

I don't know whether the problem has been solved or not but apparently the problem might have been with the file size that was being copied over. I formatted my usb drive in NTFS and then I could move the file. What is strange is that the input/output error was being given on a file with a size just over 1GB and usually the space error for large files is given when is more than 4GB in win. Ubuntu probably works differently.

---

### Post by ibjsb4 on 2013-05-12
> yes I did, that one has all the files inside as well, is it there anyway to not get that folder when deleting files?

Yes, again in Nautilus

[ATTACH=CONFIG]242521[/ATTACH]

---

### Post by cpu2007 on 2013-05-13
great, I'll check that out tonight.

There's one more abnormal behavior that I've noticed; when I copy files in the usb flash drive, after the file is copied, the light on the USB flash drive keeps blinking like is still receiving data or something. On win the usb led would only blink when there was some sort of access to the usb but in this case the once the led starts blinking then it doesn't stop, unless I eject it from the OS using the eject option.

Is this a bug?
Thanks

---

### Post by ibjsb4 on 2013-05-13
> after the file is copied, the light on the USB flash drive keeps blinking like is still receiving data or something

Thats normal, the download is not finished until the usb stops blinking.  A download is stored in your computer ram cache and then loaded to usb.  The program thinks the download is finished because it has completed the load to ram cache, but usb's are slow and it takes a few more seconds for it to complete.

---

### Post by cpu2007 on 2013-05-13
but it takes a lot more then a few seconds to stop the blinking.
I have to eject it in order to stop it from blinking. I waited more than 15-20 secs

---

### Post by ibjsb4 on 2013-05-13
Then you must have a lot of ram.  Take a look at the original file size and the size on the usb.  If you pulled it out while still blinking I think the usb will not of completed and the file size on the usb is a bit smaller.

---

### Post by cpu2007 on 2013-05-13
yes I do have a lot of ram (8GB).
Does that mean that there's no way to have a more accurate user interface when copying a file into the USB?
I can get away when copying files into usb flash drives that have a blinking led as the led would tell me when the process is over but what about the ones that don't have the led?
Isn't there anyway to make it synchronous?

---

### Post by ibjsb4 on 2013-05-13
Don't pull it out.  Use the eject or safe remove option in Nautilus.  If its still loading, this way it will say so.

---

