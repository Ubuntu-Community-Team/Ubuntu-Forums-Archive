---
title: "Are there any known issues with 8.10 and K3b?"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by L Campbell on 2008-10-10
I'm running 8.10 Beta on a PC and wanted to burn a CD, so I installed K3b from Synaptic.

It tells me that it can't find a CDROM (or words to that effect) on my machine, although the CDROM shows up in BIOS, where I have set it to boot first.

Is this a known issue with 8.10?

TIA.

---

### Post by jemate18 on 2008-10-10
> **L Campbell said:**
> I'm running 8.10 Beta on a PC and wanted to burn a CD, so I installed K3b from Synaptic.

It tells me that it can't find a CDROM (or words to that effect) on my machine, although the CDROM shows up in BIOS, where I have set it to boot first.

Is this a known issue with 8.10?

TIA.

When you haven't installed K3B, where you able to access your CDROM?

---

### Post by phidia on 2008-10-10
> **L Campbell said:**
> I'm running 8.10 Beta on a PC and wanted to burn a CD, so I installed K3b from Synaptic.

It tells me that it can't find a CDROM (or words to that effect) on my machine, although the CDROM shows up in BIOS, where I have set it to boot first.

Is this a known issue with 8.10?

TIA.

You don't need k3b. The file manager can write using the optical drive.
Just right click on the data or image file(s) you want to burn and select "Write to Disc..".

The backend to the gui writing/burning tools is wodim (see man wodim) and you can use that command line tool to find out what's going on with your drive.

---

### Post by rbmorse on 2008-10-10
What phida said, but for the record k3b works fine on Intrepid here.

---

### Post by ronacc on 2008-10-10
I use k3b in intrepid (gnome) and it works fine used it the other day to burn a couple of iso's .

---

### Post by L Campbell on 2008-10-10
> **phidia said:**
> You don't need k3b. The file manager can write using the optical drive.
Just right click on the data or image file(s) you want to burn and select "Write to Disc..".

The backend to the gui writing/burning tools is wodim (see man wodim) and you can use that command line tool to find out what's going on with your drive.

Thanks for your interest.

I did this and INSTANTLY, when I clicked on 'Write', the bar turned gold and the message said 'Completed writing".

No doubt this wasn't supposed to happen?   :-)

---

### Post by ronacc on 2008-10-10
it will do that if it don't see a writeable media in the drive  and if it don't see the drive at all it isn't seeing a writeable media .

---

### Post by cariboo on 2008-10-10
Have you tried going to Settings-->Configure K3b to see if your device shows up their. I usually add all the programs that k3b would like to see by going to Settings-->Configure k3b-->Programs. The only thing I don't add is Emovix, because I have never been able to find it in any repositories.

---

