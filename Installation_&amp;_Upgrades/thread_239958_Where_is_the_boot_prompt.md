---
title: "Where is the boot prompt?"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by plshelpme on 2006-08-20
I am planning on typing noapic nolapic in the boot prompt but where exactly is it? Do i type *boot: noapic nolapic* on the boot options box in the splash screen? I am so confused because I have spent two days trying to install this thing and I haven't done my paper yet. ](*,) ](*,) 

This is because I am installing the latest Edubuntu and after it says "Adding live user" at the installation screen it says "Uncompressing Linux... Ok, kernel boot" or something like that at the top and then the screen just goes blank.:confused: :( :-k ](*,)

---

### Post by Cynical on 2006-08-20
What motherboard chipset do you have?

By the way its *boot: kernel noapic nolapic*

---

### Post by scxtt on 2006-08-20
if you're talking about a live CD, there should be a listing that says "Options" and requires you to press a function key {something F1 --> F6, not sure which} ... otherwise you have to edit your grub entry before grub boots the OS ...

---

### Post by plshelpme on 2006-08-20
I have to press F6 while "Start or Install Edubuntu" is selected and then an input box at the bottom appears reading Boot Options: <and then a lot of other stuff here. basically the directory i think> -- *is this where i put boot: kernel noapic nolapic?*

and then press enter?

is that right?

---

### Post by plshelpme on 2006-08-20
[IMG]http://i8.tinypic.com/254xypu.png[/IMG]
[http://i8.tinypic.com/254xypu.png](http://i8.tinypic.com/254xypu.png)

---

### Post by scxtt on 2006-08-20
there's no harm in trying ;) ...

and i think you just tack them on to the end of what's already there, not sure - only did it once and it was more experimentation than anything else ...

---

### Post by plshelpme on 2006-08-20
thanks a lot. im going to try and put them at the end (boot: kernel noapic nolapic)

thank you both. :D

---

### Post by plshelpme on 2006-08-20
still did not work. i'm giving up.

---

### Post by scxtt on 2006-08-20
i really doubt you need the 'kernel' or the 'boot:' ... just tack the options onto the end ...

---

### Post by plshelpme on 2006-08-20
i tried erasing"quiet" and tacking "nolapic" at the end. Instead of Uncompressing Linux... Ok, booting the kernel I got stuck at a directory listing and command list of some sort.

---

