---
title: "Has Anyone Got gaim-Rhythmbox To Work With gaim2?"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by Mark76 on 2006-10-10
Anyone? :???:

---

### Post by jonojono on 2006-10-10
While I do not use Ubuntu, I know there are people using Gaim-Rhythmbox on Ubuntu with the Gaim 2.xbeta series.

The version that works with the 2.x series can be found here:
[http://jon.oberheide.org/projects/gaim-rhythmbox/]("http://jon.oberheide.org/projects/gaim-rhythmbox/")

What is your specific problem?

---

### Post by Mark76 on 2006-10-11
I can't get it to work.

I don't think.

How would I know if it's working or not?

---

### Post by jonojono on 2006-10-11
That's one of the most vague responses I've ever seen.  ;)  I would suggest reading the README and following the installation steps and if you determine a more specific issue that you need help with, please let me know.

---

### Post by Skerit on 2006-10-20
I compiled it, I can activate it in the plugin window but it doesn't do an awful lot, %rb still sayd %rb in my nickname, it doesn't show the currently playing song...

---

### Post by jonojono on 2006-10-21
Can you save the output of gaim -d and attach it to the forum?  Make sure to change the song in rhythmbox a couple times before ending the capture so we can diagnose any problems.

---

### Post by Anonii on 2006-10-22
It doesnt work in me, too.

I just installed it to test it out. I compile it, alright. I activate it. Add %rb to my name, and I just see an %rb in my name, not the title of the song or anything. I, also, added my email on my contact list to check it out, and my name is "Anonii %rb" (if we say that my nickname is Anonii.).

(It works in MSN, right?)

---

### Post by jonojono on 2006-10-22
Gaim-Rhythmbox uses the provided Gaim API to set presence information for each protocol.  For setting status information (see status.h) it uses gaim_status_set_attr_string() on the "message" attribute.  For setting user information it uses the account API (see account.h).

I created an account with MSN to test with and MSN doesn't seem to have support for status/away messages.  The only configuration thing I can see is the "friendly name" attribute.  In addition, looking at the code for the MSN protocol plugin in Gaim, it doesn't seem to use the standard status API.

So there's two options for those who want MSN support: submit a patch to Gaim to change the MSN protocol to use the status/account API, or, submit a patch to Gaim-Rhythmbox to add explicit support for that protocol using the internal MSN functions to set the desired status information.

---

### Post by Anonii on 2006-10-23
> **jonojono said:**
> Gaim-Rhythmbox uses the provided Gaim API to set presence information for each protocol.  For setting status information (see status.h) it uses gaim_status_set_attr_string() on the "message" attribute.  For setting user information it uses the account API (see account.h).

I created an account with MSN to test with and MSN doesn't seem to have support for status/away messages.  The only configuration thing I can see is the "friendly name" attribute.  In addition, looking at the code for the MSN protocol plugin in Gaim, it doesn't seem to use the standard status API.

So there's two options for those who want MSN support: submit a patch to Gaim to change the MSN protocol to use the status/account API, or, submit a patch to Gaim-Rhythmbox to add explicit support for that protocol using the internal MSN functions to set the desired status information.
Thank you for describing the problem, even if i dont know what API is, and what these attributes are. 

Do you know if amsn, supports a rhythmbox plugin?

Thanks again!

---

### Post by jonojono on 2006-10-23
A quick google search revealed this thread:

[http://www.ubuntuforums.org/showthread.php?t=150032](http://www.ubuntuforums.org/showthread.php?t=150032)

---

