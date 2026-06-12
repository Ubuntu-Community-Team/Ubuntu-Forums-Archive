---
title: "Initial install of 14.04 - 15 secs after sign-in screen shifts and system hangs"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by Tony_Bennett on 2014-07-17
I just installed 14.04 64-bit on an Emachine with AMD Athlon II X2 235e
with a Nvuidia GeForce 6150SE nForce 430 graphics adapter.

The install went fine, I got the grub screen fine, I got the "sign-on" window
just fine.  I entered the username and password, and the screen cleared,
and displayed the "colored" user X-Window (with Ubuntu 14.04 LTS logo at the
bottom left of the screen)... then in about 15 seconds (usually without displaying
the icon bar on the left) the screen skews with diagonal lines, and it hangs.

At this point it is non-responsive to "CTL-ALT-F1 (thru F6)... and I have to 
power cycle it.

If, however, I do not log in, but instead press CTL-ALT-F1 I can login to a terminal.
But as soon as I go back to the X-window sign-on, and sign-on the same thing
happens again.

Since I'm on a low-speed DSL, I elected to do the install without automatically getting
updates.  But I have since done an "sudo apt-get update;sudo apt-get upgrade"...
...which worked, but didn't change anything.

I must admit I'm a bit of a neophyte in debugging these kind of issues so I'm at 
a bit of a loss as to where to start.

Any help would be appreciated.

-tony

---

### Post by ibjsb4 on 2014-07-18
> I'm a bit of a neophyte in debugging these kind of issues
So am I when it comes to trouble shooting other peoples video :) and thats what I suspect.  So I cannot give you a good answer, but thought this link may help.  Good luck

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvuidia+GeForce+6150SE+nForce+430+&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvuidia+GeForce+6150SE+nForce+430+&sa=Search&cof=FORID:9)

---

### Post by Tony_Bennett on 2014-07-18
Solved as follows:

  - Re-installed - no change
  - Performed:
       ```

- sudo apt-get update
- sudo apt-get install nvidia-current-updates

```

   - rebooted... everything worked

Note: Nouveau driver is used by default... after installing nvidia-current-updates 
         the nvidia driver was used.

---

### Post by ibjsb4 on 2014-07-18
Nice going :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

