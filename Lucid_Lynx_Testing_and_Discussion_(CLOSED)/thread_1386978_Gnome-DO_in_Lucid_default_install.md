---
title: "Gnome-DO in Lucid default install?"
date: 2010-01-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Luke has no name on 2010-01-21
It's such an easy-to-use, intuitive program that really helps keep my fingers on the keyboard, which is especially helpful with laptop usage. It learns your most commonly used commands, and can detect bookmarks, look up word definitions, and send suspend/restart/logout commands to the computer. A simply great tool for controlling your computer. It can do much more than what I use it for or have described; for a full description check out [http://do.davebsd.com/](http://do.davebsd.com/). 

Given its simplicity, power, low bug count, and usability benefits to the Ubuntu experience, I believe it should be included in the default installation of Ubuntu 10.04. 

(For you Mac dock lovers, it can mimic the dock interface very well, too)

---

### Post by juancarlospaco on 2010-01-21
[**Kupfer**]("apt:/kupfer"): *Python Monoless Plugin-enabled lightining fast Gnome-Do*

---

### Post by Dragonbite on 2010-01-21
I must not be using Gnome-DO correctly then.  All I get is type an application name, and click to run... I'm doing something wrong I think!

---

### Post by Hetor on 2010-01-21
No.

---

### Post by Keyper7 on 2010-01-21
I love Do with all my heart, but the average user uses the mouse much more than the keyboard, so I'm not sure it qualifies for a default Ubuntu install.

> **Dragonbite said:**
> I must not be using Gnome-DO correctly then.  All I get is type an application name, and click to run... I'm doing something wrong I think!

Click? As in *mouse* click? You're not supposed to do that.

> **juancarlospaco said:**
> [**Kupfer**]("apt:/kupfer"): *Python Monoless Plugin-enabled lightining fast Gnome-Do*

"Python" is a matter of preference.

"Monoless" is an irrelevant adjective for non-zealots.

"Plugin-enabled" is something applicable to Do.

"Lightning fast" is too subjective, any convincing benchmarks?

So far you're not giving any convincing reasons to even *check* Kupfer.

---

### Post by juancarlospaco on 2010-01-21
> **Keyper7 said:**
> 
"Python" is a matter of preference.

"Monoless" is an irrelevant adjective for non-zealots.

"Plugin-enabled" is something applicable to Do.

"Lightning fast" is too subjective, any convincing benchmarks?


[Python is built-in on the LSB]("http://dev.linuxfoundation.org/navigator/browse/intlang.php") and Ubuntu.

Monoless i mean for Slowness of that code, and disk space needed, 
i dont have problems with GPL licence on Mono, but Performance and lightweight.

Random example, SQLite has been ported to Mono, its x6 slower than normal SQLite.

Dont check Kupfer if you dont want to, even dont use Ubuntu if you dont want to.

I dont try to convince you...

---

### Post by joey-elijah on 2010-01-21
> **Dragonbite said:**
> I must not be using Gnome-DO correctly then.  All I get is type an application name, and click to run... I'm doing something wrong I think!

Preferences > Plugins 

You can do allllllll sorts with GNOME Do - post to twitter, search your files, post images to various sites, search Google... Very powerful!

> **Luke has no name said:**
> It's such an easy-to-use, intuitive  program that really helps keep my fingers on the keyboard, which is  especially helpful with laptop usage. It learns your most commonly used  commands, and can detect bookmarks, look up word definitions, and send  suspend/restart/logout commands to the computer. A simply great tool for  controlling your computer. It can do much more than what I use it for  or have described; for a full description check out [http://do.davebsd.com/](http://do.davebsd.com/).  

Given its simplicity, power, low bug count, and usability benefits to  the Ubuntu experience, I believe it should be included in the default  installation of Ubuntu 10.04. 

**(For you Mac dock lovers, it can mimic the dock interface very well,  too)**

The Dock interface is being removed (see:[http://www.omgubuntu.co.uk/2009/10/gnome-do-docky-no-longer-part-of-gnome.html](http://www.omgubuntu.co.uk/2009/10/gnome-do-docky-no-longer-part-of-gnome.html) & [http://www.omgubuntu.co.uk/2009/10/future-of-docky-interview-with-docky.html](http://www.omgubuntu.co.uk/2009/10/future-of-docky-interview-with-docky.html) for that old news )

Good news is there will be integration between Docky and GNOME Do again.

---

### Post by phrostbyte on 2010-01-21
I removed gnome-panel in my setup and I use gnome-do's docky interface for task switching / running apps, tilda for a fast console, and compiz for various window management tasks. All of it is hidden by default, so 100% of my desktop space for apps, there is no toolbars or anything persistant on the screen at all. I love this. :D

But I still wouldn't say it should be default, because gnome-do is still quite buggy. There is some known critical bugs, like gnome-do crashing every now an them on session start. I wrote a script that works around this by invoking gnome-do multiple times, but it's a major hack. And other not as serious but still annoying bugs involving icons.

---

### Post by Keyper7 on 2010-01-21
> **juancarlospaco said:**
> [Python is built-in on the LSB]("http://dev.linuxfoundation.org/navigator/browse/intlang.php") and Ubuntu.

So? We are talking about Lucid, and Mono is already shipped by default in Ubuntu.

> **juancarlospaco said:**
> Monoless i mean for Slowness of that code, and disk space needed, i dont have problems with GPL licence on Mono, but Performance and lightweight.

Python is interpreted while Mono has the benefits of JIT, this argument doesn't really fly.

Plus, I never noticed any performance problems with Do.

Any *reliable* benchmarks or technical arguments, or are you just repeating FUD you heard somewhere else?

> **juancarlospaco said:**
> Random example, SQLite has been ported to Mono, its x6 slower than normal SQLite.

The normal SQLite is a C application and irrelevant to this discussion.

Give me an example of Python being faster than Mono, that would be more relevant.

> **juancarlospaco said:**
> Dont check Kupfer if you dont want to, even dont use Ubuntu if you dont want to.

I dont try to convince you...

You are clearly advertising kupfer. I am merely pointing out that, with the current arguments, the ad is not being very efficient.

---

### Post by phrostbyte on 2010-01-21
> **Keyper7 said:**
> 
Python is interpreted while Mono has the benefits of JIT, this argument doesn't really fly.

There is nothing theoretically keeping Python from being as fast as Mono or Java. Python has a JIT'er too (Psyco) but I don't know why it doesn't seem to be commonly used. I still think Mono's jitter is a bit faster then Psyco at this point. Google is trying to make Python significantly faster  with their unladen-swallow project. And there is also a project to run Python on Mono (oh noes :D). It might make sense at some point for Ubuntu to run Python code on Mono anyway. That way you don't have to bundle a separate interpreter.

---

### Post by Keyper7 on 2010-01-21
> **phrostbyte said:**
> There is nothing theoretically keeping Python from being as fast as Mono or Java.

Maybe, perhaps I should've been less blunt in this argument. But my main point is that there's nothing inherent slower in Mono, so the performance argument is not convincing.

> **phrostbyte said:**
> Python has a JIT'er too (Psyco) but I don't know why it doesn't seem to be commonly used.

IIRC, it does not work in 64-bit architectures, this might be one of the reasons.

> **phrostbyte said:**
> And there is also a project to run Python on Mono (oh noes :D). It might make sense at some point for Ubuntu to run Python code on Mono anyway. That way you don't have to bundle a separate interpreter.

IronPython is still behind CPython in most benchmarks, but its performance improves with each release.

---

### Post by juancarlospaco on 2010-01-21
> **Keyper7 said:**
> So? We are talking about Lucid, and Mono is already shipped by default in Ubuntu.
Python is interpreted while Mono has the benefits of JIT, this argument doesn't really fly.
Plus, I never noticed any performance problems with Do.
Any *reliable* benchmarks or technical arguments, or are you just repeating FUD you heard somewhere else?
The normal SQLite is a C application and irrelevant to this discussion.
Give me an example of Python being faster than Mono, that would be more relevant.
You are clearly advertising kupfer. I am merely pointing out that, with the current arguments, the ad is not being very efficient.

hahahahaha, i never say the word *"convince"*.

Check the roadmap and mail-list, they are thinking of option to replace Tomboy with Gnote,
but cant because no real contender for F-Spot ATM, to gain space on the CD.

I say Gnome-Do is slower than Kupfer, i dont comparing programming languages,
just interested on speed and performance, **rewrite it on Assembler i will use it.**
BTW Python can be JIT if you want to.

Theres no performance problems with Do.
Theres no performance problems with Kupfer.
But Kupfer is Faster.

Im not clearly advertising kupfer.
i never say the word *"advertising"*

---

### Post by Keyper7 on 2010-01-21
> **juancarlospaco said:**
> hahahahaha, i never say the word *"convince"*.

When did I claim you did so?

> **juancarlospaco said:**
> Check the roadmap and mail-list, they are thinking of option to replace Tomboy with Gnote,
but cant because no real contender for F-Spot ATM, to gain space on the CD.

In other words, Mono is not going away for Lucid. My point exactly.

> **juancarlospaco said:**
> I say Gnome-Do is slower than Kupfer, i dont comparing programming languages,
just interested on speed and performance, **rewrite it on Assembler i will use it.**

Yes, you are comparing programming languages. Your explicitly said that Mono has worse performance.

And for the record, writing in Assembly provides no guarantee of superior performance, it has to be written *properly*.

> **juancarlospaco said:**
> Theres no performance problems with Do.
Theres no performance problems with Kupfer.
But Kupfer is Faster.

Either add "in my personal experience and opinion" or add technically relevant benchmarks to that statement.

As it is, it's meaningless.

> **juancarlospaco said:**
> Im not clearly advertising kupfer.
i never say the word *"advertising"*

So... an advertisement is only an advertisement if it explicitly contains such word?

---

### Post by Psumi on 2010-01-21
I'm not affected by this as I install via gnome-core or xfce4 or kde when on the mini.iso. But I say no to GNOME-Do.

---

### Post by juancarlospaco on 2010-01-21
So both are right, include both.
and gnome-shell, gnome-journal, back-in-time and ubuntu-manual.
:)

---

### Post by Keyper7 on 2010-01-21
> **juancarlospaco said:**
> So both are right, include both.
and gnome-shell, gnome-journal, back-in-time and ubuntu-manual.
:)

Just to be clear, I have nothing against kupfer.

I was merely trying to figure out if there was any factual advantages to it. :)

---

### Post by juancarlospaco on 2010-01-21
But like Launchy on windows*(free)* and Mac Launcher*(built-in)* are not the most used programs on every platfrom.
:)

---

### Post by Stan_1936 on 2010-01-21
> **Luke has no name said:**
> ...Given its simplicity, power, low bug count, and usability benefits to the Ubuntu experience, I believe it should be included in the default installation of Ubuntu 10.04....

From my experience with it, it greatly slows down older and/or slower systems.  If Ubuntu comes pre-installed with this waste of space, its Minimum System Requirements will have to be raised.

No.

---

### Post by Psumi on 2010-01-21
> **Stan_1936 said:**
> From my experience with it, it greatly slows down older and/or slower systems.  If Ubuntu comes pre-installed with this waste of space, its Minimum System Requirements will have to be raised.

No.

and/or they will tell people to use the cli mini.iso more.

---

### Post by SKLP on 2010-02-23
> **phrostbyte said:**
> There is nothing theoretically keeping Python from being as fast as Mono or Java. Except of course for the fact that Python is a dynamically typed language, whereas C# and Java use static typing. 
Dynamic typing generally incurs a performance penalty at runtime.

---

### Post by the yawner on 2010-02-23
While Gnome-DO is a great program, I think it's better off as just an option. It's because it introduces a different approach on communicating with your desktop; and that approach, compared to point and click, needs a little bit of unlearning and/or mentoring.

I remember trying out Katapult when I was checking out KDE a couple of years back. I was scratching my head after I've clicked the program in the menu and this little window appeared. I did not have the slightest idea on what to do with it.

---

