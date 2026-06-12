---
title: "open-source seems to be for windows"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by bayonetblaha on 2008-05-27
I'm very interested in installing the open source combat simulator project, but all the available downloads are for windows.  I can't even find anyone to contact and ask how to get it on ubuntu.  Maybe someone more familiar with sourceforge's ways can help me out.

Edit: [combat simulator project]("http://sourceforge.net/projects/csp")

---

### Post by Rallg on 2008-05-27
I haven't a clue, but I responded so that you don't think nobody read your post.

Many programs, especially multimedia and graphics-intensive programs (games), are "bolted" to the operating system. The software might specifically rely on DirectX or some Windows-only technology. Attempts to port it to Linux (or even Mac) might require profound re-writes of the code. Attempts to use intermediate software (emulation, etc.) might cause loss of functionality, or more likely would cause such a slowdown in performance that the purpose of the software would be defeated.

Ubuntu (generally, Linux) does have a program called WINE, which allows many Windows programs to run. WINE is a separate download. However, I expect that performance will suffer for your purpose. Whether or not the program is open-source, is immaterial. That simply means that people can see the program's source code, for the supported platform.

UPDATE: Below, forestpixie informs us that there is an unanswered post team. I didn't know that!

---

### Post by forestpixie on 2008-05-27
> I haven't a clue, but I responded so that you don't think nobody read your post.

There is an unanswered post team that takes care of that :)

I did look when I saw the post and yes it does appear that it is a win app, it might work through wine as said - or if you have a win disc maybe a virtual machine, depending on whether its' 3d or not

---

### Post by bayonetblaha on 2008-05-27
I'm sorry to anyone who read my post, I meant to include a link to [the program I'm talking about]("http://csp.sourceforge.net/"), but I forgot.  That probably would have improved my response.  

I am especially puzzled since the wiki includes screenshots of the game running on XP and linux, and the game is listed as "Operating System: All 32-bit MS Windows (95/98/NT/2000/XP), All POSIX (Linux/BSD/UNIX-like OSes), Linux"

As a side note, is it even possible for a program to be open-source and use directX? Seems contradictory, at least.

---

### Post by howlingmadhowie on 2008-05-27
have a look here:

[http://csp.sourceforge.net/wiki/Building_from_source_on_Linux]("http://csp.sourceforge.net/wiki/Building_from_source_on_Linux")

---

### Post by bayonetblaha on 2008-05-27
aha, not sure how I missed that.

Maybe I'll do some wiki'ing for the next schmuck who's looking for that

thanks!

---

### Post by ShodanjoDM on 2008-05-27
Hmm, seems interesting. I'll see if I can get it to work in Hardy by compiling it.

You may want to use this [link]("http://sourceforge.net/svn/?group_id=17780") instead of the link provided in the wiki page. I've checked both and found that the sourceforge's SVN has the most recent revision.

---

### Post by forestpixie on 2008-05-27
Glad you're sorted now 

@Rallg - I didn't know either until I found out :)

---

