---
title: "Mono in 9.10"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by efef on 2009-10-14
I saw a month ago that it was the plan to upgrade mono from 2.0 to 2.2 with the new ubuntu release. However, on the new features page I dont see this listed, so im wondering which version that ships with 9.10?

---

### Post by Joe_Bishop on 2009-10-14
It would be good to remove mono-runtime and all related laggy stuff at all.

---

### Post by directhex on 2009-10-14
> **efef said:**
> I saw a month ago that it was the plan to upgrade mono from 2.0 to 2.2 with the new ubuntu release. However, on the new features page I dont see this listed, so im wondering which version that ships with 9.10?

Mono 2.4.2.3 plus a couple of patches to fix a few bugs in that version

---

### Post by jfbilodeau on 2009-10-14
> **Joe_Bishop said:**
> It would be good to remove mono-runtime and all related laggy stuff at all.

I second that. Is there really a need for Mono in the base install?

---

### Post by -grubby on 2009-10-14
> **Joe_Bishop said:**
> It would be good to remove mono-runtime and all related laggy stuff at all.

> **jfbilodeau said:**
> I second that. Is there really a need for Mono in the base install?

Useful posts there guys.

---

### Post by Merk42 on 2009-10-14
[img]http://i.somethingawful.com/forumsystem/emoticons/emot-can.gif[/img]

---

### Post by cariboo on 2009-10-14
Please keep this thread on topic, or you know what will happen.

---

### Post by doas777 on 2009-10-14
> **efef said:**
> I saw a month ago that it was the plan to upgrade mono from 2.0 to 2.2 with the new ubuntu release. However, on the new features page I dont see this listed, so im wondering which version that ships with 9.10?

I guess I would assume that it will be 2.2 then. i prolly wouldn't list an incremental upgrade to an existing tech in the "New Features" list unless there was a major departure from the norm ( like gnome 3 or the new x-less xorg). just my thought though.And for the record, keep mono. I don't call for them to remove anyone else's favorite app framework. please do me the same favor. just remove it yourself.

---

### Post by imbjr on 2009-10-14
I hope debugging works i.e. setting breakpoints.

I'd like to try my hand at creating cross-platform GUI apps and thought of using Mono until I saw that breakpoints were being ignored.

---

### Post by doas777 on 2009-10-14
> **imbjr said:**
> I hope debugging works i.e. setting breakpoints.

I'd like to try my hand at creating cross-platform GUI apps and thought of using Mono until I saw that breakpoints were being ignored.

I had a simmilar problem, but later realized that I had not installed all the components (some are not pointed to by the 'mono-develop' package) so I had to poke around synaptic. finally found a package called debugger database or some such that cured my ills.

---

### Post by imbjr on 2009-10-14
> **doas777 said:**
> I had a simmilar problem, but later realized that I had not installed all the components (some are not pointed to by the 'mono-develop' package) so I had to poke around synaptic. finally found a package called debugger database or some such that cured my ills.

Damn, that simple? When I looked on the net for help it seemed that it was a known bug that had just been fixed in nightly builds. I didn't pursue the issue further.

Update: Well I had a look and couldn't find anything. monodevelop-debugger-gdb and -mdb were already installed.

---

### Post by doas777 on 2009-10-14
> **imbjr said:**
> Damn, that simple? When I looked on the net for help it seemed that it was a known bug that had just been fixed in nightly builds. I didn't pursue the issue further.

Update: Well I had a look and couldn't find anything. monodevelop-debugger-gdb and -mdb were already installed.

ion the process I had purged everything and then reinstalled it. not sure if that has anything to do with your error or not. good luck

---

### Post by andrewabc on 2009-10-14
[http://packages.ubuntu.com/karmic/mono-complete](http://packages.ubuntu.com/karmic/mono-complete)

Lots of mono packages when searching packages.ubuntu.com, I assume this is one of the main ones.

Version 2.4.2.3+dfsg-2
Last changelog was September 7, and July 30.

---

### Post by directhex on 2009-10-14
> **imbjr said:**
> I hope debugging works i.e. setting breakpoints.

I'd like to try my hand at creating cross-platform GUI apps and thought of using Mono until I saw that breakpoints were being ignored.

Debugging was broken in Jaunty due to a kernel race condition introduced in Jaunty's kernel (which I didn't notice during local tests as they were under Intrepid's kernel). mono-debugger 2.4.2 worked around the issue.

---

