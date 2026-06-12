---
title: "Install Question"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by Elvish Legion on 2010-09-23
I have an install question.

I have a Dell Latitude e6400, its a fine machine, but sadly I have to have windows around for school (though I am thinking it will work in a vmbox).  I've been tossing a couple of ideas around in my head and I'm curious of which is the easiest to pull off

1.  Install Ubuntu on one hard drive, and windows on another, flip the drives in and out of the laptop as needed...clearly this is the most work over time but maybe the cleanest

2. Install Ubuntu on an external hard drive partition...I've never had much luck with this in the past but I hear things have changed a lot since then.  The problem I see with this is the fact that if the drive isn't plugged in Grub could freak out (is there a way around that?)

---

### Post by pricetech on 2010-09-23
I'd do the 2 drives thing, but I'd also use VirtualBox on the Ubuntu drive with Windows as a guest OS and see if what you have to have windows for can be accomplished in that environment.

That's my opinion.

---

### Post by Elvish Legion on 2010-09-23
> **pricetech said:**
> I'd do the 2 drives thing, but I'd also use VirtualBox on the Ubuntu drive with Windows as a guest OS and see if what you have to have windows for can be accomplished in that environment.

That's my opinion.

Virtual box gives you actual access to a full OS correct? If so a VM may work, but I'm not sure as some of the work for school requires visual basic

---

### Post by QIII on 2010-09-23
You can use the Microsoft IDEs for VB (VB.NET, C#, J#...) just fine in a virtual machine.  

That's how I do my work when I need to prostitute myself to the Microsoft world when I'm moonlighting.  I use Visual Studio 2010.

You will be limited in the graphics department (acceleration wise) because of the virtual graphics controller.  You won't be designing games, will you?

Running a guest in a virtual machine is in virtually every way like running it on a physical machine, within the limitations of the virtual hardware available.  But remember:  Your recovery disk from your OEM will probably not install; if you have an OEM installation disk, Microsoft's EULA forbids using it to install the OS in a virtual environment.  Legally (and ethically) you need a full retail disk.

---

### Post by Elvish Legion on 2010-09-23
> **QIII said:**
> You can use the Microsoft IDEs for VB (VB.NET, C#, J#...) just fine in a virtual machine.  

That's how I do my work when I need to prostitute myself to the Microsoft world when I'm moonlighting.  I use Visual Studio 2010.

You will be limited in the graphics department (acceleration wise) because of the virtual graphics controller.  You won't be designing games, will you?

Running a guest in a virtual machine is in virtually every way like running it on a physical machine, within the limitations of the virtual hardware available.  But remember:  Your recovery disk from your OEM will probably not install; if you have an OEM installation disk, Microsoft's EULA forbids using it to install the OS in a virtual environment.  Legally (and ethically) you need a full retail disk.

I have a legal windows xp pro so thats not an issue...guess I'll try that route out.

---

