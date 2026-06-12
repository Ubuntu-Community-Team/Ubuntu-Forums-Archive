---
title: "Ubuntu Karmic: terminal produces weird fart like sound on autocomplete"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jward3010 on 2009-10-14
Whenever I autocomplete a command in gnome-terminal, in other words use "tab" to finish writing in the full command or location name my Dell laptop makes a horrible noise like a low buzz or a fart sound (it's hilarious when I'm out with it, and also embarrassing). It's from the PC speaker as I have standard audio completely muted.

It's counterpart in previous Ubuntu's was the annoying loud beep. I've looked at "/etc/modprobe.d/blacklist.conf" and "blacklist pcspkr" is uncommented.

Do I have to add "blacklist pcfart". I hope not.

---

### Post by jward3010 on 2009-10-14
I would like to add I'm wrong about it being an onboard PC speaker issue, the sound in fact comes through the normal stereo speakers - I know this after plugging in my headphones and something "farting" at me in the ear when I did something in the terminal, very loudly. This is my current fix, plug in headphones - at least it's not heard throughout the cafe I'm in.

---

### Post by sgage on 2009-10-14
That's not a bug - it's a feature!

:-)

---

### Post by rex4u on 2009-10-14
WOW...an ambarassing feature ;)
Just kidding...:P

---

### Post by jward3010 on 2009-10-14
It's a ridiculous feature, it's an ugly loud sound that generates looks as I type away in public, and because gnome-terminal is so noisy (you get beeps when you do autocomplete on a command that has multiple possiblilites, on paths with multiple possiblilities, when you type a non-present command (fair enough), when you backspace in nano, vi or gnome-terminal and there's no text there) I sound like a total idiot while I'm out. It's so silly it's like a prank, the "beep" was loud and bad enough but this noise (now horribly loud in my headphones) is even worse even though there has been a lot of discussion on getting rid of pcspkr unecessarily for most things.

Basically the bottom line is - How do I kill it!

---

### Post by ranch hand on 2009-10-14
I think I need a laptop so I, too, can have this feature.

---

### Post by biji on 2009-10-14
it is sound when sound card waking up from sleep (power saving) kind of annoying. muting soundcard does not solve issue

---

### Post by TrueTom on 2009-10-14
Disabling the terminal bell might work... (Edit -> Profile Preferences)

---

### Post by jward3010 on 2009-10-14
That did it, thanks a million. The digestive problems that arise when I have my laptop are now cured.

Next thing is to kill the unecessary beeping (or flatulence) in Gnome and apps that make use of it - Firefox is an example. When you use the F3 search as you type bar, if the query you're typing doesn't exist it will beep fir every wrong letter you enter. If you're a fast typist prepare to be one noisy *******. Same problems in Gedit when you backspace on an empty document, it beeps like crazy - not really the type of Linux crime that requires audible repurcussions. A well supported bug report has been filed on this, I'll try and find the link for those interested.

---

### Post by dky182 on 2009-10-16
you could try disabling the audible bell in compizconfig under general options. it should work

---

### Post by jward3010 on 2009-10-16
Cheers, I'll give that a try when I'm back with my laptop. Is it a compiz specific sound?

---

### Post by moloch42 on 2009-10-16
The following worked for me:

Go to System>Preferences>Sound and then to the "Sound Effects" tab. There is a slider there called "Alert Volume." Muting this slider eliminated the sound everywhere that I have encountered it.

---

