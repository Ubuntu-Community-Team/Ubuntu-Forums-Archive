---
title: "Jockey not working"
date: 2008-08-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-08-18
Hi,

I haved installed Intrepid today, to start testing. For some reason jockey doesn't seem to launch, so I can't install my nvidia card's drivers. nvidia-glx-new doesn't seem to appear in synaptic either, only some packages with, seemingly, version numbers on them.

Are you getting the jockey problem too? What package must I install?

---

### Post by aamukahvi on 2008-08-18
> **Bou said:**
> Hi,

I haved installed Intrepid today, to start testing. For some reason jockey doesn't seem to launch, so I can't install my nvidia card's drivers. nvidia-glx-new doesn't seem to appear in synaptic either, only some packages with, seemingly, version numbers on them.

Are you getting the jockey problem too? What package must I install?
I think they're moving away from having Jockey install the video drivers. Try checking the package descriptions (there's a list of supported chips) in Synaptic and install the most appropriate one?

---

### Post by ronacc on 2008-08-18
go to system>administration>hardware drivers , the nvidia drivers will be shown there , check the one you want and it will download and install it , note that to use compiz you will have to run it from the terminal or use fusion icon ( its in synaptic) to start it and you will have to restart it each login , somethings are not autostarting right now .

---

### Post by cariboo on 2008-08-18
I've got an Nvidia 6150 and compiz now works all the time without having to restart every time I boot up. I did have a problem with jockey-gtk not downloading any drivers. I had to go into synaptic and download the nvidia-glx-177 module manually but after that the driver was enabled and I'm getting the maximum resolution for my monitor.

Jim

---

