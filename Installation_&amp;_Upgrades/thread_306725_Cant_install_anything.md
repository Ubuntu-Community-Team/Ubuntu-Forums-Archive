---
title: "Cant install anything"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by Rmag37 on 2006-11-25
I just installed Ubuntu 6.10 yesterday and cant understand how to install anything even when i read the installation instructions it just doesn't make any sense for instance i am trying to install limewire and i went to the installation guide this is what i got:

All Other Platforms - Type: jre -cp LimeWireOther.zip install. *If the above does not work try: jre -classpath [path to] classes.zip: LimeWireOther.zip install. If that does not work either, on sh-like shells, try: cd [to directory where install.zip is located] CLASSPATH = [path to] classes.zip: LimeWireOther.zip export CLASSPATH java install. For csh-like shells try: cd [to directory where LimeWireOther.zip is located] setenv CLASSPATH [path to] classes.zip: LimeWireOther.zip java install Once you have installed the LimeWire program, your next step will be bringing up the application. Do this by clicking on the LimeWire entry in the program menu of your start menu. *requires local JRE or JVM install with command: java -classpath LimeWireOther.zip install.

That just doesn't make sense can somebody simplify it using lamens/windows terms? I also have noticed that i cant play MP3 files or WMA files, i downloaded some music and they are all mp3 and wmas, what files can i play and is there a program i can use to find those?

---

### Post by futz on 2006-11-25
Go to [http://www.getautomatix.com/](http://www.getautomatix.com/) and get Automatix2 installed. Just follow instructions on their install page.

That will allow you to install Frostwire, which is almost exactly the same as Limewire. They're the same code, almost. Automatix will also allow you to install the codecs you need for mp3's and various movie formats, as well as lots of other goodies.

Oh ya, sounds like you'll need JRE (Java Runtime) installed. Automatix does that too.

---

### Post by Rmag37 on 2006-11-25
Oh cool thanks so i can play wmas and mp3s after i get the codecs?

---

### Post by futz on 2006-11-25
> **Rmag37 said:**
> Oh cool thanks so i can play wmas and mp3s after i get the codecs?
Yes.

I'm not positive about wma's as I don't see many of those, but I don't remember being unable to play *anything*.

You may have to install totem-xine to get totem to work. I forget. But you can do that with Synaptic. Once that's set up and you have all the codecs, there's almost nothing you can't play.

---

### Post by Rmag37 on 2006-11-25
Cool i can play all Mp3s (i think) and some WMAs (dont as why) anybody know of a good media player? One thats similer to Windows Media Player 11? i liked the interface and everything about it, except the bug that made you reboot if you browsed through the library when watching a music video, but thats besides the point.

---

### Post by futz on 2006-11-25
For video, totem-xine (aka: Movie Player in the Applications/Sound & Video menu. But the ubuntu stock totem uses gstreamer, which is young and not so good yet. Replace gstreamer with xine and totem really shines.). There are plenty of others, like mplayer and vlc. Some people like them. I like totem. It will play music too.

For music, amarok. It's porky and slow, but very nice. For a lightweight quick to use player, try xmms or beep. Again there are lots of others that might suit you better. Try em all.

---

### Post by Rmag37 on 2006-11-25
Cool thanks for the help.

---

