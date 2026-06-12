---
title: "Nvidia driver issue"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nandus1 on 2009-02-28
Hello all,
I am having an issue enableing Nvidia drivers in Jaunty. 
When I click on the activate option, it appears that it is trying to run the installer, but stops at "0%" and closes the window.

After having this issue with all of the available drivers listed in " Hardware drivers", I downloaded the latest installer from Nvidia's site. 

Ubuntu will not run the installer when I enter in the run command listed on Nvidia's site ("sh NVIDIA-Linux-x86-180.29-pkg1.run"). 
The package is located on the desktop.

Note: I had the driver installed and running fine with Ibex and Compiz enabled.
I ran into a similar issue upon refomatting w/ Ibex, so I am unsure if it is just an issue w/ Januty.

Any thoughts?


System info:
Asus P4S800 Mobo, ECS 6600LE AGP card w/ 3.0Ghz P4 ht, 1 gig DDR 400.

---

### Post by RedSingularity on 2009-02-28
Did you go to the directory your downloaded file is in? In your case it should be "cd ~/Desktop/NVIDIA-Linux-x86-180.29-pkg1.run" in the terminal

Then run the file from there.  "sh NVIDIA-Linux-x86-180.29-pkg1.run"

---

### Post by Nandus1 on 2009-02-28
It will not go to the directory that I downloaded the package to.
The option to select the directory is "greyed out".

I was kind of stumped by that to tell you the truth. 

I am going to format over Jaunty w/ Ibex and see if my luck changes.

Thank you for your reply.

---

### Post by overdrank on 2009-02-28
Moved to Jaunty Jackalope Testing and Discussion

---

### Post by cariboo on 2009-03-01
I had the same problem when I reinstalled about a week ago, just install the driver from the repository. Then activate it using System-->Administration-->Hardware drivers.

I don't know if it is just me, but the main server has been really slow for the last couple of weeks, just as slow as the main Canadian server. :)

Jim

---

### Post by ubu-for on 2009-03-06
> **cariboo907 said:**
> I had the same problem when I reinstalled about a week ago, just install the driver from the repository. Then activate it using System-->Administration-->Hardware drivers.

Today I had the same problem with the German server.

---

### Post by mistypotato on 2009-03-06
Same here today ...

cannot seem to activate the driver

---

### Post by Bakon Jarser on 2009-03-12
Just installed alpha 6 and have the same problem.  All nvidia drivers are installed in synaptic but none of them will activate.  I hit the activate button and a progress bar comes up for a couple of seconds then disappears.  Has a bug report been filed for this?

---

