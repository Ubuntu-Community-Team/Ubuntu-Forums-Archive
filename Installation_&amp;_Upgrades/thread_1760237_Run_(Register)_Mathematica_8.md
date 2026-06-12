---
title: "Run (Register) Mathematica 8"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by timopheym on 2011-05-16
I'd install and activate programm Mathematica 8 on my ubuntu (10.04, Gnome 2.30.2).
But when i treid to run it, i get message about registration like this:
[IMG]http://krasnyjugolok.ru/cant.png[/IMG]
The bug is, that I CAN'T press any button. And then i close the window programm cloasd too. 
I treid press enter, space, double click... it does not work at all!
What is it? What can i do? Does any body know something about this trange thing?

---

### Post by psych787 on 2011-07-07
With a working installation, I produced the following configuration file. Try placing the following in ~/.Mathematica/FrontEnd/init.m - that should prevent the registration dialog from appearing at all.

```

SetOptions[$FrontEnd, 
Current2DTool->"Select",
Default2DTool->"Select",
Current3DTool->"RotateView",
Default3DTool->"RotateView",
PrivateFrontEndOptions->{"LicensesAgreed"->{"8."}},
VersionsLaunched->{"8.0.1"},
PrivateFrontEndOptions->{"DialogSettings"->{
 "DialogSettings" -> "None", 
  "WelcomeScreen" -> {
   "ShowRecentFilesContextMenu" -> False, "DefaultSlideNumber" -> 5, 
    "CurrentSlideNumber" -> 5}},
"LastRegistrationReminderDate"->None,
"ShowAtStartup"->"NewDocument"}
]

```

--Technical Stuff--

I had the same problem described above. For no apparent reason, the registration dialog just started working. Possibly a reinstall helped, possibly not.

Also, Mathematica's tech support is *awesome*, and amazingly competent with linux tools including strace and gdb. They were extremely helpful, and gave me permission to post this. However, they did warn the workaround may not work on future versions of Mathematica.

---

### Post by NSim on 2011-11-10
Hi,

I tried this solution and it overwrites the registration panel, but when mathematica starts , I am having the same problem, I cannot click, double-click, keyboard...nothing.The startup screen freezes like the registration panel  Is there any solution to this?

Thanks

---

### Post by rewyllys on 2011-11-10
> **NSim said:**
> Hi,

I tried this solution and it overwrites the registration panel, but when mathematica starts , I am having the same problem, I cannot click, double-click, keyboard...nothing.The startup screen freezes like the registration panel  Is there any solution to this?

Thanks
I recommend that you contact Mathematica's Tech Support people.  Explain the problem to them, and ask for their suggestions.  As already mentioned in this thread, they are very helpful and knowledgeable.

---

### Post by titis on 2011-11-11
I found the problem...is the license

If the license end with :10 the Registration Page will not respond any click

---

### Post by AIQ on 2012-08-04
> **NSim said:**
> Hi,

I tried this solution and it overwrites the registration panel, but when mathematica starts , I am having the same problem, I cannot click, double-click, keyboard...nothing.The startup screen freezes like the registration panel  Is there any solution to this?

Thanks
This is rather late, but I had the same problem. The configuration file provided above got me past the registration screen, but then I was stuck again. Substituting 8.0.1 -> 8.0.0 in VersionsLaunched got everything working.

---

### Post by astrobob.tk on 2012-10-14
None of what I found online worked even this thread.

What did work though is installing Mathematica 7 (of course if you have the this version) then installing Mathematica 8.

This solved the problem & now it's working normally.

Hope this helps someone.

---

