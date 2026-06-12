---
title: "System beep on restart/shutdown, remove from final"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by forcecore on 2009-04-19
I think that restart/shutdown beep should be removed because it is NOT NEEDED and blews up speakers and is reaaaallly annoyng, yesterday it woke up half a house when my s90 russian speakers had on half power after watching movie.

i know it can be removed with blacklisting but it should be blacklisted by default.

---

### Post by keep-on-smiling on 2009-04-19
yep I agree with this, especially as I get 2 beeps running together - heck I even turn off the actual login/logout sounds....

cheers

---

### Post by rajeev1204 on 2009-04-19
Ya can anyone tell me how to disable those?

My speakers are also gonna blow up .Is the speaker inside the cpu also being used?

Annoying since intrepid i think.

---

### Post by ktp on 2009-04-19
[http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/](http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/)

---

### Post by jongkind on 2009-04-19
> **ktp said:**
> [http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/](http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/)

Nope, this does not work anymore for Jaunty. A fix is committed (but not released yet).

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331589]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331589")

---

### Post by forcecore on 2009-04-19
so i assume it is fixed in final and it should because it is so easy and do not change features but just removes that TERROR beeping BinLaden.

---

### Post by paradigm2 on 2009-04-19
I believe there is also a bug causing it to beep multiple times and send multiple warning messages over the console.  I presume this is not helping matters.

---

### Post by mdurham on 2009-04-19
Does anyone know what is the point of this *feature*, does it serve any purpose at all?

---

### Post by forcecore on 2009-04-19
someone should call to Shuttleworth or main head developer to remove this from final.

and yes there is no good purpose of this beep horror.

---

### Post by mdurham on 2009-04-19
Also, what is the point of the "are you sure you want to reset/shutdown" dialog? I just clicked 'shutdown', of course I'm sure. This is just adding things for the sake of it. What a waste of time!

---

### Post by olskar on 2009-04-19
> **mdurham said:**
> Also, what is the point of the "are you sure you want to reset/shutdown" dialog? I just clicked 'shutdown', of course I'm sure. This is just adding things for the sake of it. What a waste of time!

I agree! But you can deactivate that ;) Just rightclick on the userswitcherapplet and preferences

---

### Post by forcecore on 2009-04-19
> **mdurham said:**
> Also, what is the point of the "are you sure you want to reset/shutdown" dialog? I just clicked 'shutdown', of course I'm sure. This is just adding things for the sake of it. What a waste of time!

this is useful because there are several times i canceled my shutown process if i forgot something.

---

### Post by mdurham on 2009-04-19
> **olskar said:**
> I agree! But you can deactivate that ;) Just rightclick on the userswitcherapplet and preferences

Thanks olskar, why didn't I think of that?
Cheers, Mike

---

### Post by JohnFante on 2009-04-20
> **paradigm2 said:**
> I believe there is also a bug causing it to beep multiple times and send multiple warning messages over the console.  I presume this is not helping matters.

I have the multiple beep error. Rather annoying - to say the least.

---

### Post by rajeev1204 on 2009-04-20
Ok problem solved for me by adding blacklist pcspkr to /etc/modprobe.d/blacklist.

I had to create the file as it didnt exist.My PC is so peaceful now :)

---

### Post by FuturePilot on 2009-04-20
> **rajeev1204 said:**
> Ok problem solved for me by adding blacklist pcspkr to /etc/modprobe.d/blacklist.

I had to create the file as it didnt exist.My PC is so peaceful now :)

/etc/modprob.d/blacklist has been moved to /etc/modprobe.d/blacklist.conf

I also agree. The beep on shutdown or reboot is annoying. It always scares me because it's so loud. I've actually had pcspkr blacklisted since Intrepid.

---

### Post by rajeev1204 on 2009-04-20
> **FuturePilot said:**
> /etc/modprob.d/blacklist has been moved to /etc/modprobe.d/blacklist.conf

I also agree. The beep on shutdown or reboot is annoying. It always scares me because it's so loud. I've actually had pcspkr blacklisted since Intrepid.


Hmm i noticed now blacklist.conf. strangely the file /etc/modprobe.d/blacklist seems to work too as that is where i put that line.

---

### Post by FuturePilot on 2009-04-20
> **rajeev1204 said:**
> Hmm i noticed now blacklist.conf. strangely the file /etc/modprobe.d/blacklist seems to work too as that is where i put that line.

Yes it will work, but don't expect it to work forever. I got a deprecation warning once that said something like all blacklist files must now end in .conf or they will be ignored in future versions. Just a heads up ;)

---

