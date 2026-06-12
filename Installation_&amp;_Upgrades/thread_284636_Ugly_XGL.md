---
title: "Ugly XGL"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by kdub432 on 2006-10-25
I just did a fresh upgrade to edgy from dapper. I had beryl/xgl working on dapper. After sucessfully installing xgl onto edgy, i noticed that all the windows have an ugly,grey,boxy feel to them, unlike the standard GNOME sesson. XGL running on dapper didnt have this. Any idea how to get edgy looking nice again while using xgl?

---

### Post by woedend on 2006-10-25
uhm, why are you using XGL with edgy if i may ask?  its unnecessary as AIGLX is built in, assuming you use the right drivers.  What vid card do you have?

---

### Post by kdub432 on 2006-10-26
I am using a radeon 9600 pro. I tried to use beryl with aiglx, but it doesnt work. I get a 

kevin@kevin-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

type of error, when I try.

---

### Post by goldenatom on 2006-10-26
Did you check out this [guide]("http://doc.gwos.org/index.php/BerylOnEdgy")? I think it is a little more difficult on ATI hardware. I got it running on my Ti4200 without too much pain.

---

### Post by skyfisher on 2006-10-26
And when you mention "ugly, grey, boxy feel", do you mean that windows are using the default gnome theme for buttons and window dress-up? Are you able to switch (gtk) themes?

---

### Post by kdub432 on 2006-10-26
I think i am using the gnome defaults... any idea how to change it to gtk?

---

### Post by skyfisher on 2006-10-26
Try loading gnome-settings-daemon (add it to your session startup programs, if necessary).

---

### Post by goldenatom on 2006-10-26
What does that do?

---

### Post by kdub432 on 2006-10-26
Worked like a charm. Thanks skyfisher!

---

### Post by skyfisher on 2006-10-26
@goldenatom: For one, it enables theming and font support.

@kdub432: Excellent! :)

---

### Post by mrfuzzemz on 2007-01-24
> **skyfisher said:**
> Try loading gnome-settings-daemon (add it to your session startup programs, if necessary).

Just wanted to thank skyfisher as that solved a problem that I've been too lazy to deal with for too long.

---

