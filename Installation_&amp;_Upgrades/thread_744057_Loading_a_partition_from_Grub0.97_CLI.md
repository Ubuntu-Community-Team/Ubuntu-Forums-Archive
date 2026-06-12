---
title: "Loading a partition from Grub0.97 CLI"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by Serpreme on 2008-04-03
I'm using Grub to load a script that asks a image server if there is work to be done. But the problem is, once the script runs, it sets the OS to load upon next boot up, restarts and it takes awhile for the whole process to go through.
I'm just wondering if i can execute grub after the script runs, have grub run, put in a command like chainloader (hd1,0)+1 and have the OS load next. Bypassing a total reboot.
I'll try to answer any questions i can. thanks for any help.

---

### Post by Serpreme on 2008-04-03
Here is my problem now!
I've found that if i do:
```
rootnoverify (hd0,1)
makeactive
chainloader +1
boot
```
From the grub command line selected from the menu list,it loads windows just fine. But if i run a script,it has its own kernel loaded, and it just kicks back to a prompt. 
So i suppose my new question is this:

How can i make it exit the shell/kernel i load from GRUB and allow it to just load the OS?

Edit: fixed a little grammar.

Basically i want the initrd OS to exit and load the windows OS. Now that i put it like that, i may need something else. 
Or i may need to load a script shell from inside grub. Or load a kernel/OS thats purpose is to just run a script, and load a partition as its OS.
My, that sounds easy.

---

### Post by Serpreme on 2008-04-04
I'm now trying out Kexec. Seems to be a fun little command.
So far i loaded a new kernel, but i'm not sure which one it is. I think it was the vmlinuz-generic one. Everything looks different. 
But the system hard froze, so its not a great success yet.

---

### Post by dstew on 2008-04-04
> i'm using Grub to load a script that asks a image server if there is work to be done.You lost me here. How do you get grub load and execute a script?

---

### Post by Serpreme on 2008-04-04
Sorry, i dont, its loading a kernel that loads a script automatically.

---

### Post by dstew on 2008-04-04
> once the script runs, it sets the OS to load upon next boot upThis probably has something to do with the savedefault statement. In the grub manual, there are some sections that have to do with [fallback menu items]("http://www.gnu.org/software/grub/manual/grub.html#Booting-fallback-systems"), maybe you can set up grub to work that way. There is also the section above on booting once only. Just a thought.

---

### Post by Serpreme on 2008-04-07
Hmm i looked into that, it appears that would come into play if it failed to load the entry. But it doesnt fail, it works wonderfully in that regard.
I wonder if i could feed it a command that would make it look like it failed, and load the other option.
Or if this is even possible since it probally hands off control to the OS it loads.
Maybe i'm ,wrong.
I've looked into kexec, but it doesnt seem to be widely supported. I cant seem to find any working examples of windows being able to load correctly. 
Next thing i am going to look into is Two Monte system or something along those lines.

---

### Post by dstew on 2008-04-07
Did you check the ["Boot Once Only" section of the grub manual]("http://www.gnu.org/software/grub/manual/grub.html#Booting-once_002donly")? You modify the grub menu item, so that it automatically boots another item the next time it runs, even if the first choice ran correctly. Would this help? It seems using the grub command 'default saved', and then modifying the menu.lst items with different savedefault values might help.

---

### Post by Serpreme on 2008-04-07
Community,
I believe i have explained my problem incorrectly. It happens without any coffee.

My situation is this.

Grub loads, 
It kicks in a kernel that runs a script that checks a image server for work to do.

Depending on the return, it will either do the work, or it will write to the menu.lst and have it load the current partition that has windows on it.

the problem is, it edits the menu.lst through a minimal GRUB CLI. The only way to make the menu change take effect i have seen is to reboot.

So what happens is, in order for it to load to windows, it has to go through and load an additional OS just to see if its alright to load windows. Which is time consuming when you factor in the bigger picture of thousands of computers being effected by this.

So I'm trying to work Kexec or something along thos lines into having it pass control on to windows, bypassing the reboot to load the new menu.lst.

So basically i need some way to load GRUB again, or load windows again. Either will work, but both seem problematic in achieving.

I'm so new to Linux and this process that one of my issues is explaining the problem correctly. But I'm working at it everyday and this is something i want to become good with.

Thanks for any time you've spent reading my plight!

---

### Post by dstew on 2008-04-07
> it edits the menu.lst through a minimal GRUB CLI.You mean a kernel (operating system) is loaded, and that operating system runs a script that edits grub through a grub command line? Why not alter the script to edit the menu.lst file using a text editor?

---

### Post by Serpreme on 2008-04-07
Well, it does a conditional.
Depending on the response it gets from the image server, it will either load the orginal menu.lst or it will load the partition.
I've followed the code, and the problem is that it goes Grub ---> kernel ---> Runs grub command and sets it up so it loads the partition next.

I could have that mistaken, but i do know it loads the kernel, runs the commands. I've repeated them, and when i finish, it brings me to a prompt. It doesnt load the partition. Sadly.
If i do the option to load the partition in the menu.lst, it will boot right into windows. But only if its from the GRUB CLI you get from hitting esc and pressing control C(Or is it just C?)

Hope that makes sense.

---

### Post by dstew on 2008-04-07
Would you mind posting the script? Also, I am unsure of your vocabulary. What do you mean by "loads the partition"? If you are referring to grub, it boots operating system kernels, either by loading and booting a kernel image, or by chainloading. By "loading the partition" do you mean grub chainloading?

---

### Post by Serpreme on 2008-04-08
Actually, i was browsing and i believe Grub4Dos will be able to help me out a lot in this part.
As i said partition, i do mean the windows OS, for some reason it says Activepartition. So it makes me think to say partition each time i think about it.

---

