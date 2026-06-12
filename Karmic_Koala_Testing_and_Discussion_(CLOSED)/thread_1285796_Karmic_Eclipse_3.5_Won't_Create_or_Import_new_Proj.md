---
title: "Karmic Eclipse 3.5 Won't Create or Import new Projects"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by RJG on 2009-10-08
I've just installed the beta of Karmic Koala after my 9.04 died on me (ATI drivers, what fun).

However, Eclipse is being a pain in that it's not allowing me to import or create new projects. Whenever I click on "next" or "finish" it just sits there and does nothing.

Is there a simple solution or is this a beta problem?

---

### Post by HubertD on 2009-10-08
Same problem here.
Creating new projects won't work with the karmic eclipse packages, nor with the gtk download versions of galileo :-(

---

### Post by ambarish.chaudhari on 2009-10-09
Hi,

I had the same problem. I think the issue is with Gtk recognizing the button-click events.

Work-around: click on the "Next" / "Finish" buttons and then press <enter> or <space>.

Annoying, but works for now. 

I still need to check if there is a bug for this already. Also if this is problem with Eclipse build or with other Gtk apps like Gimp, etc. (I haven't faced any so far!)

Thanks,

-ambarish

---

### Post by Drood on 2009-10-09
Wow, I had almost the exact same thing happen, and I was just about to make a post. Messed around with ATI drivers on 9.04 (seem to be better on 9.10 btw)and destroyed some graphical component of ubuntu ( <=newb ) so I decided to prematurely install 9.10, install eclipse, now I am trying to install the visual editor plugin through either update or install new software and it doesn't do anything when clicking on next or finish.  This proved as a solution, thanks.

---

### Post by UnSandpiper on 2009-10-09
Same issue here.

Can only "click" the buttons using the keyboard shortcuts "alt + something".

Does anyone know if there is a bug report in launchpad?
At least I couldn't find anything...

Also the new way of reporting bugs in launchpad is a pain.
I have this issue only with newer versions of Eclipse which are not in repos, so ubuntu-bug doesn't let me report a bug for that. 
Also, not sure if this is a Eclipse or rather GTK bug... :confused:

---

### Post by Joe_Bishop on 2009-10-09
Don't use eclipse from repos.

---

### Post by TrueTom on 2009-10-09
> **Joe_Bishop said:**
> Don't use eclipse from repos.

Doesn't work with the offical releases either...

---

### Post by Joe_Bishop on 2009-10-09
> **TrueTom said:**
> Doesn't work with the offical releases either...
Everything is OK for me

---

### Post by lithorus on 2009-10-09
> **Joe_Bishop said:**
> Everything is OK for me
I'm using the official version and I have the same problem as the original poster. Which version are you using? 3.5.1? I believe it used to work fine in 3.5.0.

---

### Post by jou770d on 2009-10-09
Did you have to do anything special to get eclipse to start???
For me, it just hangs on the splash screen after asking me for the workspace location. Tried removing and reinstalling both eclipse and java but nothing changed.

---

### Post by ma2k1 on 2009-10-09
For me Eclipse doesn't work neither from repo neither the official release.
It's a pain... Impossible to install plugins, manage projects etc...

There is a bug in launchpad?

---

### Post by HubertD on 2009-10-09
Really seems to be some missing click events, the workaround with using the spacebar / enter to select buttons is ugly, but works for me.

---

### Post by !nkubus on 2009-10-09
Same Issue here with Eclipse pdt and Zend Studio, I have to use netbeans at the moment. I hope it's going to be fixed soon

---

### Post by lithorus on 2009-10-09
It's a problem with GTK and eclipse.
Found this bug : 
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257](https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257)

Edit:
a fix is to use
```
export GDK_NATIVE_WINDOWS=true
```before launching eclipse.

---

### Post by HubertD on 2009-10-09
thx, works for me!

---

### Post by dinxter on 2009-10-09
> **lithorus said:**
> It's a problem with GTK and eclipse.
Found this bug : 
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257](https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257)

Edit:
a fix is to use
```
export GDK_NATIVE_WINDOWS=true
```before launching eclipse.

thanks lithorus, i've been wondering about that one

---

### Post by lean on 2009-10-09
Thx for the solution, I guess this should be handled in upstream Eclipse?

---

### Post by RJG on 2009-10-09
An odd bug, and as a newbie I'm not sure how to report it (or if it already has). Thanks for the help and the work-arounds guys.

---

### Post by lithorus on 2009-10-10
> **RJG said:**
> An odd bug, and as a newbie I'm not sure how to report it (or if it already has). Thanks for the help and the work-arounds guys.
Basically it is already reported.

---

### Post by dinxter on 2009-10-10
> **lithorus said:**
> Basically it is already reported.
is there a launchpad bug watching upstream? its a good idea if not

---

### Post by dinxter on 2009-10-10
ah, there it is, and fixed in -ubuntu2, super
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/443004](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/443004)

---

### Post by cororok on 2009-10-10
I fixed it with making a simple shell script

I'm using a binary eclipse of [www.eclipse.org](www.eclipse.org)


// Make a script inside eclipse folder
eclipse.sh
```

export GDK_NATIVE_WINDOWS=1
./eclipse

```

---

### Post by lithorus on 2009-10-11
> **cororok said:**
> I fixed it with making a simple shell script

I'm using a binary eclipse of [www.eclipse.org]("http://www.eclipse.org")


// Make a script inside eclipse folder
eclipse.sh
```

export GDK_NATIVE_WINDOWS=1
./eclipse

```
Then you have to be in the eclipse folder to execute it.

Anyway the quickfix also seems to fix some other issues aswell (when installing new plugins the list items are invisible).

---

### Post by apiper on 2009-10-23
I installed Karmic yesterday, and found that was unable to use any of the searches in the "Search" menu - until I found this thread. Thanks cororok!

---

