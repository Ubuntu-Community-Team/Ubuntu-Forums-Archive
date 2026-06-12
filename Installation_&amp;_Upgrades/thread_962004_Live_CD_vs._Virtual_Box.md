---
title: "Live CD vs. Virtual Box"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by vtech81 on 2008-10-28
Just wondering which would be faster, a Live CD or Virtual Box (or any other virtual OS program). Sorry if the answer is obvious, I'm a newbie. 
For a virtual OS I have 1gb RAM, so I'd probably give it 512mb. I'm not sure what my CD drive read speed is, it's a pretty new computer, but nothing special.

---

### Post by geezerone on 2008-10-28
VirtualBox without a doubt - no CD would have read access as fast as hard drive access. The versatility of virtual OS (being able to save/restore OS) is a strong point too.

You don't need to set 512MB for VB prob 384MB tbh.

---

### Post by vtech81 on 2008-10-28
Ok, that's what I was hoping so I wouldn't have to go through the pain of using a disk and a USB for persistence. Thanks for the quick reply.

---

### Post by vtech81 on 2008-10-29
Another question. Wubi, or virtual box? Because I've heard wubi is pretty fast.

And how would I install Virtual Box on my external hard drive? I'm trying to use Ubuntu at school, but of course I can't install  that on their computer :( or my hard drive for that matter seeing as their bios doesn't support boot from usb. Any advice for optimizing performance on a crappy school computer would be great. And yes, I have permission from my teacher to do this, as long as I don't screw up the computer.

Wubi installs a file in the boot folder in Windows that lets you dual boot, right? If I do this with my schools computer, would it do anything drastic to the computer (like mess up the MBR)?

---

### Post by vtech81 on 2008-10-29
Also, is there a way to get compiz-fusion working through the Ubuntu VirtualBox? I want to show some of my friends the cool things Linux can do.

---

### Post by ahuman on 2009-02-11
I'm interested in the answer to your question. -Bumper

---

### Post by snowpine on 2009-02-11
> **ahuman said:**
> I'm interested in the answer to your question. -Bumper

Desktop effects don't generally work in VirtualBox, as the virtualized machine does not have direct access to your graphics card.

---

### Post by zwygart on 2009-02-11
No, Wubi don't changes anything in the MBR. I never used wubi. But I think this will not screw the computer. Installing after may be. Compiz, I don't know. Install compiz-settings-manager and activate 3D support on VB. 

ahuman : Why are you getting alive an old thread?

---

### Post by unixeducation on 2009-02-11
I really don't recommmend doing anything like what you're describing with a school computer. I'm just trying to keep you out of trouble; people get in serious messes by modifying school and work machines.

Unfortunately, virtualization software must be installed on the computer you're using it on; it can't simply be run from external media.

Perhaps you could ask your school's network administrator if there's a specific computer they'd be okay with you experimenting on. That would be the best approach, I think.

---

