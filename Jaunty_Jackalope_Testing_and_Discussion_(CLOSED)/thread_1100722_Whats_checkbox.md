---
title: "Whats checkbox ?"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-03-19
Hi

What does checkbox do? Never seen it before.Nor does it run on my system.

Many new things in jaunty it seems ,like system janitor.

---

### Post by taavikko on 2009-03-19
```
Description: Checkbox System Testing
 This project provides an extensible interface for system testing. The results
 can then be sent to Launchpad.


```

---

### Post by pferraro on 2009-03-19
> **rajeev1204 said:**
> Hi

What does checkbox do? Never seen it before.Nor does it run on my system.

System->Administration->System Testing

---

### Post by rajeev1204 on 2009-03-19
> **pferraro said:**
> System->Administration->System Testing


I said it doesnt run and crashes on my system, so i dont know what it looks like.

Sorry if you missed that.

---

### Post by taavikko on 2009-03-19
> **rajeev1204 said:**
> I said it doesnt run and crashes on my system, so i dont know what it looks like.

Sorry if you missed that.

Sorry, just read through the lines...

Does launching via CLI run it?
```
checkbox-gtk
```
It's tool to send hardware info to launchpad.

---

### Post by Halow on 2009-03-19
Both ways crash for me. It's already been bugged:

[https://bugs.launchpad.net/checkbox/+bug/344916](https://bugs.launchpad.net/checkbox/+bug/344916)

---

### Post by philinux on 2009-03-19
Seems to run here ok, report sent off. However it did not ask any questions about stuff working like it says in the gui.

---

### Post by SketchyClown on 2009-03-19
Works flawlessly here.

---

### Post by rajeev1204 on 2009-03-19
> **taavikko said:**
> Sorry, just read through the lines...

Does launching via CLI run it?
```
checkbox-gtk
```
It's tool to send hardware info to launchpad.


Ya it starts from CLI but apport catches a crash always. But i got a window to test hardware.

Then when i say click on finish it again crashes.Seems like a py-gtk error.
Hmm buggy code i could fix that .

Dont really have time to fix bugs as yet . :)

---

### Post by Sprut1 on 2009-03-19
How ironic :)

---

