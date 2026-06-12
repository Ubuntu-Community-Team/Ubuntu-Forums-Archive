---
title: "Pidgin has no sound"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Toadinator on 2008-10-21
Ever since I upgraded to Intrepid Pidgin has had no sounds at all. Flash and media players (like songbird) work absolutely fine, but for Pidgin (and SCUMM VM as well) there isn't any sound. I tried the guide to get pulseaudio working in here somewhere but nothing's working. What should I do, did I do anything wrong?

---

### Post by anhvu2875 on 2008-10-21
**Toadinator**
Pidgin : Tools > Preferences > Sounds

---

### Post by Eisenwinter on 2008-10-21
Also, though this message looks dumb, Pidgin does not play sounds when your status isn't set to "Available".

---

### Post by Toadinator on 2008-10-22
> **anhvu2875 said:**
> **Toadinator**
Pidgin : Tools > Preferences > Sounds

I already tried that. No sound. Nada. Zip. Zilch.

---

### Post by anhvu2875 on 2008-10-23
**Toadinator**
try to restart Pidgin .

---

### Post by danf_1979 on 2008-10-23
> **Toadinator said:**
> I already tried that. No sound. Nada. Zip. Zilch.

You maybe hitted CTRL+S without knowing. It happend to me :). Go to "Tools -> Mute Sounds", uncheck it if checked. Cheers.

---

### Post by Toadinator on 2008-10-23
> **danf_1979 said:**
> You maybe hitted CTRL+S without knowing. It happend to me :). Go to "Tools -> Mute Sounds", uncheck it if checked. Cheers.

Already did that; still no sound.

---

### Post by Toadinator on 2008-10-25
> **Toadinator said:**
> Already did that; still no sound.

....and still the problem persists :-\

I'd REALLY appreciate it if someone decided to help me over here.

---

### Post by meho_r on 2008-10-25
Do you have any options as "Sound Methods" (Preferences > Sound)?

---

### Post by Yashiro on 2008-10-25
- Open a Terminal. Do pulseaudio -vv.
What does it say? If there are errors you need to fix those.

- If not, do the 'login' 'logout' sounds on the gnome sound properties applet work?

- If you have working sounds on other apps and gnome sounds work, chances are it's a Pidgin only issue.

- Open 'alsamixer' from a terminal, set PCM Master and PCM Fronts to MAX.

---

### Post by Toadinator on 2008-10-25
> **Yashiro said:**
> - Open a Terminal. Do pulseaudio -vv.
What does it say? If there are errors you need to fix those.

- If not, do the 'login' 'logout' sounds on the gnome sound properties applet work?

- If you have working sounds on other apps and gnome sounds work, chances are it's a Pidgin only issue.

- Open 'alsamixer' from a terminal, set PCM Master and PCM Fronts to MAX.

thanks, but no thanks. it actually fixed itself after a couple of updates lol. anyways if anything else doesn't work then i'll use that thing you just said. thanks!

---

### Post by ftmichael on 2008-10-26
I'm having the same issue, having just upgraded to Intrepid RC; the sound in Pidgin will work fine initially, even with Audacious playing at the same time (in Hardy they wouldn't both work simultaneously and I had to kill pulseaudio every time I started X).  Restarting Pidgin gets me the sound back, but that's a huge pain for me because I'm always in a bunch of IRC channels and don't want to be leaving and returning constantly.

**sudo pulseaudio -vv** gave me:

```
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_7fc_sound_card_0_alsa_playback_0"): initialization failed.
```

And a load of other stuff, but that was it for errors.  All the other lines started with **I:** or **D:**.

Also, something that's enormously helpful for me - errors showing up in bold red text in the terminal.  Makes it a whole lot easier to scroll through stuff and find them.

I tried running **pidgin -d** in the terminal, but got a ton of:

```
dbus: The signal "blist-node-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
dbus: The signal "conversation-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
```

... every time I switched to a new tab (I keep several IRC channels open at once in tabs).  It, along with all the other stuff Pidgin was doing - updating the buddy list and so on - scrolled so much that I couldn't see anything else.  When the sound did die, I looked through the terminal quickly before it scrolled so far that I couldn't see back far enough.  I found no errors relating to sound.

**ETA:** Solved!  See SadaraX's post immediately below mine.  It's a workaround really, not a fix, but it suits me just fine.  No need to install aplay separately if you have ALSA.

Michael

---

### Post by SadaraX on 2008-10-26
I think I have a solution for you, provided you have ALSA on your system (and you probably do).

Go to Pidgin -> Tools -> Preferences -> Sound

For the "Method" select 'Command'

The text input box below should become enabled. Type this in there:

aplay %s

This will pass your Pidgin sound through the ALSA play program.

I have never tried using PulseAudio or anything else with Pidgin, since none of them have ever worked for me. This is the only solution I know of or have needed for years. I don't know if you need to install aplay or if it comes with ALSA.

Good luck.

---

