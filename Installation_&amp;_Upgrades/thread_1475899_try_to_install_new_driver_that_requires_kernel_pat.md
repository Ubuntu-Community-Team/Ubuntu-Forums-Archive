---
title: "try to install new driver that requires kernel patch"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by mr.thraz on 2010-05-07
i have a [prodikeys pc-midi]("http://www.prodikeys.com/") 

after abandoning windows for Ubuntu my prodikeys has been solely a qwerty keyboard. 

i just found a linux [driver]("https://sourceforge.net/projects/pc-midi-linux/") for it.

but his installation instructions call for a kernel patch.

i was going to try and do it myself,

but after going to [this page]("https://help.ubuntu.com/community/Kernel/Compile") i thought that might not be a good idea.

it states:

> Reasons for NOT compiling a custom kernel
_***You merely need to compile a special driver. For this, you only need to install the linux-headers packages.***_
You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratch.
You got to this page by mistake, and checked it out because it looked interesting, but you don't really want to learn a lot about kernels.


i was wondering how i would go about using the headers to install this driver?

---

### Post by mr.thraz on 2010-05-07
pics of my [mixxx rig]("http://picasaweb.google.com/mrthraz/DAWLove?feat=directlink#5432098240655754514") and my [Ubuntu-studio daw]("http://picasaweb.google.com/lh/photo/-1ctF5fnzKPS-iaZPHpQvw?feat=directlink").

a creative way to bump, but, also to give extra info in-case you still don't know what the heck i'm talkin' about in the above post.

---

### Post by mr.thraz on 2010-05-07
anybody?

---

### Post by mr.thraz on 2010-05-08
once again

---

### Post by mr.thraz on 2010-05-08
help

---

### Post by mr.thraz on 2010-05-08
please

---

### Post by mr.thraz on 2010-05-08
someone

---

### Post by mr.thraz on 2010-05-08
does no one know?

can you maybe point me to someone who would?

---

### Post by mr.thraz on 2010-05-09
anybody

---

### Post by gazj on 2010-05-09
You will need to recompile the whole linux kernel.  There are detailed instructions in the README file that come with the driver

I could do this on my version of linux, but I really dont know how to recompile the kernel in ubuntu.  Ubuntu tends to add a layer of complecity to a kernel build, look up building custom kernel for ubuntu in google.

---

### Post by mr.thraz on 2010-05-10
> **gazj said:**
> You will need to recompile the whole linux kernel.  There are detailed instructions in the README file that come with the driver

I could do this on my version of linux, but I really don't know how to recompile the kernel in Ubuntu.  Ubuntu tends to add a layer of complexity to a kernel build, look up building custom kernel for Ubuntu in Google.

you didn't quite answer my question.

i read the read me and i understand it.

i also read in this site where it was said that i should not recompile the kernel for a new driver install, i should instead use the header file to do that.

I'm just asking if anyone knows how to use the kernel header instead of the kernel, since thats what the link and quote at my first post seems to say i should do.

---

### Post by mr.thraz on 2010-05-11
wow

---

### Post by danh-a on 2010-10-16
> **mr.thraz said:**
> wow

Mr. Thraz --- did you ever get an answer?

I also ran across that page which basically says if
you want to compile a special driver then
"you only need to install the linux-headers packages".

That page is at:
   [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
but has far as i can tell it doesn't give the faintest
clue as to actually how to install the linux-headers
packages.

If you look in the synaptic package manager, there seem
to be about a dozen packages whose names start with
linux-headers.

So i think that an additional link on the Kernel/Compile
page would be helpful, to some discussion about just
what we have to do.

And in the meantime i would be interested in what Mr. Thraz
or anybody else has to say on the subject.

dan

---

