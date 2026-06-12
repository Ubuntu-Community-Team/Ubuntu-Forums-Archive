---
title: "Problem upgrading from 12.02 to 14.04"
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by Peus_de_gat on 2015-06-14
I recently upgraded from 12.02 to 14.04, and now I can't log in. I input my pw, it kind of flickers and goes back to prompting my pw.

I can only access via the command line, problem is I don't really know how to use it! And, very foolishly of me, I don't have my stuff backed up so I can't just format the whole thing and start from scratch! Can someone help me with a) solving the problem or b) telling me how I can somehow get all my stuff onto an external hard drive using the command line so that I can wipe it all and start from scratch?

HELP!!!

and 

THANK YOU :D!!

---

### Post by grahammechanical on 2015-06-14
Run a Ubuntu Live session to access the hard disk to back up your files. 

Regards.

---

### Post by ubfan1 on 2015-06-14
Can you boot successfully using the oldest kernel listed under the "advanced..." grub menu choice?  Do you have any proprietary video like Nvidia on the machine?

---

### Post by UltimateCat on 2015-06-15
Hi:

To find out what graphics card you have just run this in your konsole/terminal-

```
lspci | grep -i VGA

```

---

### Post by Peus_de_gat on 2015-06-15
Hi Grahammechanical, 

Thanks for your reply! Unfortunately, I already try this, but can't access my home folder from Ubuntu Love session |
"This location could not be displayed." it says. I don't have permission to view the content of my home folder much less copy it somewhere, and I have no way of getting there (i,e, nowhere where I can input my password to get those permissions ) :(
At least no way that I know of...

---

### Post by Peus_de_gat on 2015-06-15
> **UltimateCat said:**
> Hi:

To find out what graphics card you have just run this in your konsole/terminal-

```
lspci | grep -i VGA

```

Hi UltimateCat.

This is what I get:  00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 7340]

Does that tell you something?

Thanks!

---

### Post by Peus_de_gat on 2015-06-15
> **ubfan1 said:**
> Can you boot successfully using the oldest kernel listed under the "advanced..." grub menu choice?  Do you have any proprietary video like Nvidia on the machine?

Hi ubfan, 

The only ways I can do anything right now are through the command line or using Live Ubuntu booting from a pendrive...:S

I don't know about proprietary video, but I don't think so.

Cheers :D

---

