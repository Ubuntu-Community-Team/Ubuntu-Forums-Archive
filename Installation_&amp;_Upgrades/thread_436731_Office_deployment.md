---
title: "Office deployment"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by suntin on 2007-05-08
Hi, I am considering deploying Ubuntu across the board in my office.

This would mean 1 server and 30-40 desktops.
Server isn't much of a problem, SMB shares on windows server are annoying me they respond so slowly, the only question there is what FS is going to be good should we decide to backtrack but not lose all the data in home directories.

But the desktops I need some advice with, I have a few requirements.
1) Is it possible to create a generic install routine so I can save a few hours selecting default packages, user accounts, mounted drives and shares etc....
2) We have some printers with no available linux drivers, is it possible to keep a Windows machine (preferably not within my sight) that interfaces these printers?
3) Are roaming profiles possible/viable
4) once configured is there a way to make changes to the installs (most likely packages) which will replicate to all machines?

---

### Post by veloce on 2007-05-18
> **suntin said:**
> Hi, I am considering deploying Ubuntu across the board in my office.

This would mean 1 server and 30-40 desktops.
Server isn't much of a problem, SMB shares on windows server are annoying me they respond so slowly, the only question there is what FS is going to be good should we decide to backtrack but not lose all the data in home directories.

But the desktops I need some advice with, I have a few requirements.
1) Is it possible to create a generic install routine so I can save a few hours selecting default packages, user accounts, mounted drives and shares etc....
2) We have some printers with no available linux drivers, is it possible to keep a Windows machine (preferably not within my sight) that interfaces these printers?
3) Are roaming profiles possible/viable
4) once configured is there a way to make changes to the installs (most likely packages) which will replicate to all machines?

I can't answer most of those questions, but since no one else has, I'll put in what I can.

On 2). I have a printer with no linux driver.  There are some tools that allow you to set up a windows machine with a printer to mimic a postscript printer that the linux machines can then print to.

I have heard that this also works from within a virtual windows machine.  Obviously, the windows machine must be able to communicate directly with the printer.

If the printers have a network connection then the windows machine can be anywhere, otherwise they will need to be next to the printers.

---

