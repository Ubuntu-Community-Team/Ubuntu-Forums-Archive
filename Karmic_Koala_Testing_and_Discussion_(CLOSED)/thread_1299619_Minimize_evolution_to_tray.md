---
title: "Minimize evolution to tray"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nevon on 2009-10-24
I'm running Ubuntu 9.10 and I'm wondering how you minimize Evolution to the tray applet. At first I thought it was really neat that both Empathy and evolution were in the same notification applet - but what's the point if you can't even minimize evolution?

---

### Post by k3lt01 on 2009-10-24
I agree with you on that. I have never used Evolution much before but I have set it up and it looks to be halfway decent but without being able to minimise it it is useless to me.

As a slight aside, I went back to Pidgin. Empathy just wont do what it should for me and I think it needs alot more work before it should be the main IM program.

---

### Post by Nevon on 2009-10-25
So you're saying there's no way to do it? :S Wow, how could such a vital piece of functionality have been left out of the default email client? Then what's the point of the applet in the first place?

---

### Post by andbia on 2009-10-25
I have to agree on this, i assumed on both jaunty and karmic that it would work that way... i just don't see any need for the applet since it don't bring any functionality at all, it's even more redundant on kubuntu.

---

### Post by sevenflo on 2009-10-25
I feel the same way. Strangely though, one day I used the same disc that I used for my laptop to install Ubuntu for a friend. Her evolution minimized to the tray, while mine still doesn't. I have no idea why, and it never happened again. Maybe an update? Or maybe I was actually installing Ubuntu Studio.  But it was definitely weird as I couldn't find a setting to even stop that from happening.

---

### Post by k3lt01 on 2009-10-25
> **Nevon said:**
> So you're saying there's no way to do it? :S Wow, how could such a vital piece of functionality have been left out of the default email client? Then what's the point of the applet in the first place?
Unfortunately, yes thats what I am saying. The applet will happily tell you that you have new emails but if you already have Evolution maximised you will know that anyway. So it is in effect of no use except as another way to start Evolution, Empathy, and in my case Pidgin as it also loads from it but the difference is Pidgin can still minimise easily.

I'd hazard a guess and say Thunderbird might also load from the applet and may still be a better option if it does.

---

### Post by cyberkilla on 2009-10-25
> **k3lt01 said:**
> Unfortunately, yes thats what I am saying. The applet will happily tell you that you have new emails but if you already have Evolution maximised you will know that anyway. So it is in effect of no use except as another way to start Evolution, Empathy, and in my case Pidgin as it also loads from it but the difference is Pidgin can still minimise easily.

I'd hazard a guess and say Thunderbird might also load from the applet and may still be a better option if it does.

As far as I know, it should still be possible. They cannot "close" the window, because that would close Evolution. However, there _must_ be a way to hide() a window without closing it. In Windows, you can show/hide a form, but it does not appear to be destroyed. Idk. Hard to believe that X doesn't have a way to unmap a window and take it out of the taskbar.

Bug report about it: [https://bugs.launchpad.net/ubuntu/+source/evolution-indicator/+bug/387833](https://bugs.launchpad.net/ubuntu/+source/evolution-indicator/+bug/387833)

---

### Post by stinger30au on 2009-10-25
> **Nevon said:**
> So you're saying there's no way to do it? :S Wow, how could such a vital piece of functionality have been left out of the default email client? Then what's the point of the applet in the first place?


the applet comes in handy when using multiple desktops

im my desktop one i have running firefox, lifera rss reader and evolution and thats it

everything else i do in any other desktop

when a new email arrives the mail icon changed colour and i click on it and click evolution and my screen rolls around to the email

brilliant

i then click back to the desktop i was working before i got the email and after i have read and replied to the email

---

### Post by ngsupb on 2009-10-25
Guys, the solution is simple.

Just install AllTray. It puts a program into tray.

You can modify the launch script of Evolution to put it into tray at the start by using alltray.

---

### Post by alienclone on 2009-10-25
> **ngsupb said:**
> Guys, the solution is simple.

Just install AllTray. It puts a program into tray.

You can modify the launch script of Evolution to put it into tray at the start by using alltray.

+1

or use Thunderbird with the FireTray addon

---

### Post by cyberkilla on 2009-10-25
AllTray isn't really a complete solution. Whilst it technically does put the application on the tray, it doesn't hide it entirely...

You see, with the new Indicator Applet, Pidgin, Empathy, Gwibber, etc, will not show a tray icon. Instead, they are all wrapped up inside of the Indicator Applet.

This saves space and allows for a unified way to interact with applications that support Indicator Applet.

---

However, this thread isn't specifically about minimising Evolution to the Indicator Applet, so AllTray is probably satisfactory as a solution to the original question.:P

---

### Post by iamnotthemessiah on 2009-10-25
theres a little evolution tray plugin here [http://gnome.eu.org/evo/index.php/Evolution_Tray](http://gnome.eu.org/evo/index.php/Evolution_Tray)

but i havent been able to compile it

---

### Post by Nevon on 2009-10-25
Well, I really like the new applet and think it's a great idea to unify all apps of this sort into one common applet, so to use alltray, firetray or whatever completely defeats the purpose. 

For now I'm opening Evolution and then send it to another workspace - but it's just weird that none of the developers seem to have thought of this before. Where would I file a feature request? To the indicator applet developers or to the developers of Evolution?

---

### Post by Keyper7 on 2009-10-25
> **iamnotthemessiah said:**
> theres a little evolution tray plugin here [http://gnome.eu.org/evo/index.php/Evolution_Tray](http://gnome.eu.org/evo/index.php/Evolution_Tray)

but i havent been able to compile it

I found another one here: [http://blog.sukimashita.com/?p=124](http://blog.sukimashita.com/?p=124)

The Ubuntu developers will try to fix the Evolution behavior for Lucid. I believe the main problem so far is that minimizing Evolution to tray goes directly against upstream's wishes, as it violates the Gnome HIG.

---

### Post by cyberkilla on 2009-10-25
> **Keyper7 said:**
> I found another one here: [http://blog.sukimashita.com/?p=124](http://blog.sukimashita.com/?p=124)

The Ubuntu developers will try to fix the Evolution behavior for Lucid. I believe the main problem so far is that minimizing Evolution to tray goes directly against upstream's wishes, as it violates the Gnome HIG.

Lol, but they don't mind Empathy doing it? They always shoot the idea down, I don't know why. One of the main complains of evolution.

---

### Post by Keyper7 on 2009-10-25
> **cyberkilla said:**
> Lol, but they don't mind Empathy doing it? They always shoot the idea down, I don't know why. One of the main complains of evolution.

The Gnome HIG is against a tray icon just for the sake of minimizing.

The Empathy tray icon shows user status and indicates new messages.

---

### Post by adalal on 2009-10-25
any idea on when this will be fixed by the developers?

---

### Post by k3lt01 on 2009-10-25
> **stinger30au said:**
> the applet comes in handy when using multiple desktops Thats great for some people but in cases like my father who started with multiple desktops and then wondered where everything went I had to cut it down to 1 desktop. So we are left with a need for the ability to minimise Evolution to the applet.

> **Keyper7 said:**
> The Gnome HIG is against a tray icon just for the sake of minimizing.

The Empathy tray icon shows user status and indicates new messages.
But its not just for the sake of being able to minimise, it is for ease and usability. When Evolution is open the applet tells you if you have a new message but because Evolution is already fully open you would know that anyway. If we could minimise Evolution to the applet the applet could still tell us if we have received any new messages.

If they can build Empathy, a completely useless program imho, to work with the applet that way why can't they do it for Evolution which is supposed to be a serious email agent? The excuse that they wont do it just for the sake of minimising just doesn't hold water, there are obvious benefits for productivity let alone ease of use if they would.

---

### Post by Sirron on 2009-10-25
On the file menu there's a "Close Window" and a "Quit" option.

Am I right in thinking that "Close Window" is only of use if you have duplicate windows open?

This is actually really annoying me as well.

Could the functionality of Alltray be built into the applet perhaps?

---

### Post by iamnotthemessiah on 2009-10-27
the gnome hig is a piece of sh*t then

---

