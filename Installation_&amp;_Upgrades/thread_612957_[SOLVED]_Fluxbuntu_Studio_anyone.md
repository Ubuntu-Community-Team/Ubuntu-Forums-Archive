---
title: "[SOLVED] Fluxbuntu Studio anyone?"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by LinuxSoundMan on 2007-11-14
i have quite a mission here if it hasnt already been done. i need to install ubuntu studio functionality within my fluxbuntu system. is this possible with apt-get. i know you can upgrade ubuntu (gutsy) to ubuntu studio (gutsy) but is the same possible for fluxbuntu. any advice is appreciated. thanks.

---

### Post by LinuxSoundMan on 2007-11-14
i went ahead and did the aptitude upgrade for gutsy to studio gutsy within fluxbuntu.> [http://ubuntuforums.org/showpost.php?p=3639492&postcount=7](http://ubuntuforums.org/showpost.php?p=3639492&postcount=7) i will post the results when its completed.

---

### Post by LinuxSoundMan on 2007-11-16
do not do this. it mucks up your fluxbuntu desktop by adding gnome. bad idea.  i even excluded the apt-get ubuntustudio dekstop and it still installed gnome as well as made my mouse disappear. avoid this technique.

---

### Post by Rhubarb on 2007-11-16
Ubuntu studio uses a real-time kernel (which is different to the normal gutsy kernel).
I don't know much about ubuntu studio, but presumably you would need a real-time kernel for JACK.

You may have to install the music applications individually rather than (as you found out) grabbing studio gutsy.

Keep on posting your progress here on the forums :)

---

### Post by LinuxSoundMan on 2007-11-18
indeed the software will have to be installed individually. as for the rt kernel i have no idea how to implement this with fluxbuntu. i also noticed that fluxbuntu is missing the alsa connectGUI which is essential to connect external MIDI devices to your software. if there is anyone who has info on implementing the rt kernel within fluxbuntu i would appreciate it. i posted this idea at the fluxbuntu forums and have gotten no reply yet. its very slow over there. probably because there arent many people using it yet. thanks in advance.

---

### Post by LinuxSoundMan on 2007-11-18
ok i have succeeded. i have installed the audio packages but unfortunately you cannot install the graphics and video upgrades without having gnome and metacity installed. so in order to make your fluxbuntu into an "audio" studio enter the following in terminal.

first...
> sudo apt-get update

then...
> sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt

then...
> sudo update-menus

now reboot into your new rt-kernel which will be done automatically courtesy of GRUB. and you will then boot into your brand new fluxbuntu audio studio with all the necessary audio components including jack audio and MIDI functionality. its that simple. post your experience here. kind regards to all who have helped me with this,

---

