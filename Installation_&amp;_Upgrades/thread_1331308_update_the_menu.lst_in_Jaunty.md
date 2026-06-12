---
title: "update the menu.lst in Jaunty"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by praveenthivari on 2009-11-19
I am still in Jaunty for some bugs in Karmic.
I installed it yesterday and updated it. In the end it asked me, whether I liked to keep the default grub settings or install a new one in it's place. I gave  NO. And that was the mistake I think I did. Because now menu.lst still shows the OLD kernels. 
How do I update the menu.lst to show even the new kernel which installed during the update.

I tried ```
sudo update-grub
``` But it doesn't change anything

---

### Post by darkod on 2009-11-19
You can edit it with:
sudo gedit /boot/grub/menu.lst

Copy the same entry as for the old kernel and then change it according to where the new kernel is and the title to show the new kernel.

---

### Post by praveenthivari on 2009-11-19
> **darkod said:**
> You can edit it with:
sudo gedit /boot/grub/menu.lst

Copy the same entry as for the old kernel and then change it according to where the new kernel is and the title to show the new kernel.

Thanks for the reply.
I did it.:)
I hv couple of questions more. 
1.Can I delete the Old kernel? 
   Last time I did it from Computer Janitor, ubuntu wouldn't start again. Just blinking cursor after grub menu.
2. How do I install newest kernels?

---

### Post by darkod on 2009-11-19
The kernel doesn't take too much space so I wouldn't delete it. Let it stay there for a while until you are sure there are no issues with the new one. You can even leave it in the grub menu too because if sometimes the new doesn't work you can just select the older version.

I am new to ubuntu and I haven't tried yet to update the kernel, but if you google around I am sure there are some tutorials. On different versions of linux I have used before it was as simple as executing update kernel, in ubuntu probably would be:
sudo apt-get update kernel

PS. If your question is solved it is recommended to mark the thread as solved, only you can do that. Above the first post there is Thread Tools. You can do it there. It helps other people.

---

### Post by drs305 on 2009-11-19
> **praveenthivari said:**
> Thanks for the reply.
I did it.:)
I hv couple of questions more. 
1.Can I delete the Old kernel? 
   Last time I did it from Computer Janitor, ubuntu wouldn't start again. Just blinking cursor after grub menu.
2. How do I install newest kernels?

You should be able to install new kernels by updating your repository lists and checking for new packages with:
```
sudo apt-get update && sudo apt-get upgrade
```

You can also install new kernels by opening Synaptic, press Reload, and then searching for "linux-image" to see the available kernels.

As for removing old kernels, I have some instructions on removing older kernels in this link, although I too would recommend keeping at least one older kernel that works.

[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")
Refer to the section "Removing Older Kernels"

---

### Post by praveenthivari on 2009-11-19
Thanks again,

I did read somewhere that we have to keep atleast one kernel spare. 

Ok, I was refering to newest and not the one which is provided in the repo.;)

---

### Post by Irony on 2009-11-19
> **praveenthivari said:**
> I did read somewhere that we have to keep atleast one kernel spare.
No, when you are happy the new kernel is working then uninstall the old kernel - you don't need spare kernels.

---

### Post by praveenthivari on 2009-11-19
> **Irony said:**
> No, when you are happy the new kernel is working then uninstall the old kernel - you don't need spare kernels.

Ok. So I can delete them now.
Thanks for the reply.
And wat about installing latest kernels. I am happy with the present one but just to try it.:D

---

