---
title: "Evolution in Jaunty still at Neanderthal stage"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2009-03-08
Not sure if I'm asking this in the right place but, using Evolution as an example - what happens when a core application in Jaunty has some serious bugs before release time?.

Here's a nasty Evolution one:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881)

And a non-critical, but important for heavy users:
[https://bugs.launchpad.net/evolution/+bug/255768](https://bugs.launchpad.net/evolution/+bug/255768)
[http://bugzilla.gnome.org/show_bug.cgi?id=574245](http://bugzilla.gnome.org/show_bug.cgi?id=574245)

In the case that the Evolution maintainers can't get it into shape on time, do we get the current, buggy version, or will the version in Intrepid be backported?

I'm more interested in the release process as opposed to Evolution (although I really hope it gets cleaned up!)

Thanks

---

### Post by Starks on 2009-03-08
Bad pun? Debilitating bugs? Upcoming release?

Where are the devs and maintainers when we need them?!?!?

---

### Post by olskar on 2009-03-09
> **jarlath said:**
> Not sure if I'm asking this in the right place but, using Evolution as an example - what happens when a core application in Jaunty has some serious bugs before release time?.

Here's a nasty Evolution one:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881)

And a non-critical, but important for heavy users:
[https://bugs.launchpad.net/evolution/+bug/255768](https://bugs.launchpad.net/evolution/+bug/255768)
[http://bugzilla.gnome.org/show_bug.cgi?id=574245](http://bugzilla.gnome.org/show_bug.cgi?id=574245)

In the case that the Evolution maintainers can't get it into shape on time, do we get the current, buggy version, or will the version in Intrepid be backported?

I'm more interested in the release process as opposed to Evolution (although I really hope it gets cleaned up!)

Thanks

I agree with you, that is a nasty bug. I can't imagine Ubuntu would release such a buggy version of their default mail and calendar client.

---

### Post by cl333r on 2009-03-09
Ubuntu != Fedora, but I noticed Fedora 11 taking decisions I certainly like, one of them is to move to Thunderbird 3 (beta) and I like it a lot better than Evolution btw, I also heard Fedora feels spappier and seems to not support Mono so much (which for me is good news), gonna give it a try.

---

### Post by Voynix on 2009-03-09
> **jarlath said:**
> Not sure if I'm asking this in the right place but, using Evolution as an example - what happens when a core application in Jaunty has some serious bugs before release time?.
Thanks

Sometimes I forget I have evolution open on another workspace. Strangely, it is possible to open many instances of evolution without any warnings, as there is no singleton policy and  the existing evolution window does not gain focus. I have noticed that if you open a second instance, you reset all of your passwords. Maybe the "second" evolution cannot read the passwords and decides to delete the file. I have to close down the application, and then enter the login details again. Frustrating.

---

### Post by olskar on 2009-03-09
> **Voynix said:**
> Sometimes I forget I have evolution open on another workspace. Strangely, it is possible to open many instances of evolution without any warnings, as there is no singleton policy and  the existing evolution window does not gain focus. I have noticed that if you open a second instance, you reset all of your passwords. Maybe the "second" evolution cannot read the passwords and decides to delete the file. I have to close down the application, and then enter the login details again. Frustrating.

I actually filed this multi-instance as a bug but it was closed since the developer like to use one instance of evolution with mail and another one open for calendar. This does not make any sense to me really.

Anyway, for me, it was just annoying but if this causes such problems as you get, I think you should file a bug.

---

### Post by Voynix on 2009-03-09
> **olskar said:**
> I actually filed this multi-instance as a bug but it was closed since the developer like to use one instance of evolution with mail and another one open for calendar. This does not make any sense to me really.

Anyway, for me, it was just annoying but if this causes such problems as you get, I think you should file a bug.

Cheers, it is indeed a bug if the stored passwords are likely to be wiped if you open a second instance of the application. It does not make any sense to me either, honestly.

---

### Post by calc on 2009-03-09
> **jarlath said:**
> Not sure if I'm asking this in the right place but, using Evolution as an example - what happens when a core application in Jaunty has some serious bugs before release time?.

Here's a nasty Evolution one:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881)

And a non-critical, but important for heavy users:
[https://bugs.launchpad.net/evolution/+bug/255768](https://bugs.launchpad.net/evolution/+bug/255768)
[http://bugzilla.gnome.org/show_bug.cgi?id=574245](http://bugzilla.gnome.org/show_bug.cgi?id=574245)

In the case that the Evolution maintainers can't get it into shape on time, do we get the current, buggy version, or will the version in Intrepid be backported?

I'm more interested in the release process as opposed to Evolution (although I really hope it gets cleaned up!)

Thanks

If you actually read in detail about the bugs you listed above they aren't even listed as affecting Jaunty...

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881)

This one if for Dapper (Ubuntu 6.06) and the related Intrepid issue has already been resolved in Jaunty according to the bug report in bug 270271. If it hasn't actually been resolved then the bug needs to be reopened and more information provided.

[https://bugs.launchpad.net/evolution/+bug/255768](https://bugs.launchpad.net/evolution/+bug/255768)

This bug is thought to be a duplicate of:

  [http://bugzilla.gnome.org/show_bug.cgi?id=552583](http://bugzilla.gnome.org/show_bug.cgi?id=552583)

Which is already fixed as well post Intrepid according to the upstream bug report, and if it is still happening for people in Jaunty then they should be responding to the upstream bug report as Sebastien has already requested this since he can't reproduce the problem.

[http://bugzilla.gnome.org/show_bug.cgi?id=574245](http://bugzilla.gnome.org/show_bug.cgi?id=574245)

This bug report looks like it might still affect the Jaunty version although it is filed against 2.24. If it affects you follow up to the bug report answering the developers questions. He posted a question 4 days ago and no one has responded.

Basically developers aren't clairvoyant and if they can't reproduce your bug in many instances they can't fix it. So if they ask questions it would be very helpful to answer them if you actually want the bug fixed...

---

### Post by QwUo173Hy on 2009-03-09
First of all, I apologise for the title. I though it was funny at the time but I can see how it can be seen as abuse directed at developers. I never expect fully functioning software during a development cycle so please be assured I'm not having a go at developers. Also, thanks for replying calc.

I have to put my hands up and say I didn't read the reports fully. I don't know how anything about stack traces etc., so I skip over those parts. When I saw "Affects: Evolution (Ubuntu)" I assumed it wasn't tied to any specific release - my mistake.

I don't know my way around bug-processing fully yet, but I assume, or at least I hope, I'm not offending anyone by asking questions.

The first bug, [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881) is still an issue for me, but as Sebastien says there, not to open the bug. Also, the bug he refers the poster to, [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/270271](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/270271) is titled:

"evolution crashed with SIGSEGV in g_signal_emit_valist()"

Which is a different description. Do I need to use a debugger to find out if this is my case? I don't get this output when running from the command line. If I file a new bug I'm accused of not bothering to search for duplicates so where can I ask these questions? Should I open a new bug?

---

### Post by QwUo173Hy on 2009-03-09
The terminal output on crash, doesn't contain the words "SIGSEGV" at all so I assume my issue is different.

---

### Post by Taiebot65 on 2009-03-09
I have to say evolution is becoming better and better at every release..
the only problems are the integrations with the calendar applet.....

for me it s really working randomly..

---

### Post by QwUo173Hy on 2009-03-09
Conceptually, I think it's the best PIM out there on Linux or Windows. I'd hate to have to switch. Thunderbird, as someone mentioned, is good at what it does, but Evo has some real power-user features that save me heaps of time.

We get lots of correspondence in our shop and only a small fraction of those turn into business so it's important to be able to manage time / tasks / communications as well as possible so that when business does arrive, we can drop what we're doing because we're on top of things.

I've tried everything in the repositories (for Gnome) as well as Zimbra. Evolution has all these features with the added benefit of being intergrated into the desktop. It's actually the main reason we use Ubuntu here.

---

### Post by calc on 2009-03-17
> **jarlath said:**
> First of all, I apologise for the title. I though it was funny at the time but I can see how it can be seen as abuse directed at developers. I never expect fully functioning software during a development cycle so please be assured I'm not having a go at developers. Also, thanks for replying calc.

I have to put my hands up and say I didn't read the reports fully. I don't know how anything about stack traces etc., so I skip over those parts. When I saw "Affects: Evolution (Ubuntu)" I assumed it wasn't tied to any specific release - my mistake.

I don't know my way around bug-processing fully yet, but I assume, or at least I hope, I'm not offending anyone by asking questions.

The first bug, [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/24881) is still an issue for me, but as Sebastien says there, not to open the bug. Also, the bug he refers the poster to, [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/270271](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/270271) is titled:

"evolution crashed with SIGSEGV in g_signal_emit_valist()"

Which is a different description. Do I need to use a debugger to find out if this is my case? I don't get this output when running from the command line. If I file a new bug I'm accused of not bothering to search for duplicates so where can I ask these questions? Should I open a new bug?

As he mentions in 24881 just because a bug looks similar doesn't make it the same actual bug. To determine if bug 270271 is same as yours you would need to first be able to easily reproduce the error then use gdb to get a backtrace. I believe there is information on how to do this on wiki.ubuntu.com. If the backtrace doesn't show the function names then you need to install the debug packages available from the ddebs repository also noted in wiki.ubuntu.com.

---

### Post by QwUo173Hy on 2009-03-17
> **calc said:**
> As he mentions in 24881 just because a bug looks similar doesn't make it the same actual bug. To determine if bug 270271 is same as yours you would need to first be able to easily reproduce the error then use gdb to get a backtrace. I believe there is information on how to do this on wiki.ubuntu.com. If the backtrace doesn't show the function names then you need to install the debug packages available from the ddebs repository also noted in wiki.ubuntu.com.

Thanks calc, I think I've submitted a bug already but I'll reproduce it with the packages you mentioned to see if I can get any more debug information.

---

### Post by jerrylamos on 2009-03-17
Since I run on several computers here and elsewhere I use on-line mail services with gmail, aol, yahoo.  All evolution does for me is use up space.

Jerry

---

### Post by QwUo173Hy on 2009-03-17
My business is a service so we don't have an office. We meet in various places and not all of them can provide internet connection so offline storage is vital to us. Also, our calendar extends over two years into the future so even the likes of Google Calendar Offline won't cut it there.

The Sunbird/Thunderbird combination is nice but Evolution intergrates well with Gnome. A lot of bugs I've posted have been addressed or I've at least been given a temporary workaround from a developer so things seem to be looking up for evolution.

---

