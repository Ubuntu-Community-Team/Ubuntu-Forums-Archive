---
title: "error message when trying to play midi"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-08-20
Can anyone tell me the meaning of the attached error message that I am getting when I try to play a midi file with Kmid program.  As well as this error message a get the sound which I assume is supposed to be glass breaking when I attempt to play the midi file.

Thanks.

---

### Post by christhemonkey on 2006-08-20
I cant see an attachment...

---

### Post by wpshooter on 2006-08-20
Sorry, try now.

---

### Post by christhemonkey on 2006-08-20
Have you ever been able to play midi files?


What is the output of the command:
```
aplaymidi -l 
```

---

### Post by wpshooter on 2006-08-20
No, I have never been able to get this to work to this point.  Thought I would give it yet another try this morning.

Thanks.

wpshooter@JRO-ubuntu-3:~$ aplaymidi -l
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
Cannot open sequencer - No such file or directory
wpshooter@JRO-ubuntu-3:~$ aplaymidi -1
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Cannot open sequencer - No such file or directory
wpshooter@JRO-ubuntu-3:~$

---

### Post by christhemonkey on 2006-08-20
You need to load the alsa sequencer module:
```
sudo modprobe snd-seq 
```

If that works, then do this:
```
sudo su
echo snd-seq >> /etc/modules 
logout
```

This will load the module at boot up every time.

---

### Post by wpshooter on 2006-08-20
> **christhemonkey said:**
> You need to load the alsa sequencer module:
```
sudo modprobe snd-seq 
```

If that works, then do this:
```
sudo su
echo snd-seq >> /etc/modules 
logout
```

This will load the module at boot up every time.

Can this be installed thru synaptic ?

If so, what would I search for ?

Thanks.

---

### Post by wpshooter on 2006-08-20
That stopped my from getting the error message, BUT when the Kmid player opens, it seems to be running but **NO** sound ???

Thanks.

---

### Post by christhemonkey on 2006-08-20
If you run it through a terminal does it give any output?

```
kmid /media/cdrom0/FILES.MID/AQUARIUS.MID 
```

---

### Post by christhemonkey on 2006-08-20
EDIT: Sorry double post.

---

### Post by wpshooter on 2006-08-20
NO sound.

Get this:

wpshooter@JRO-ubuntu-3:~$ cd DOWNLOAD
wpshooter@JRO-ubuntu-3:~/DOWNLOAD$ ls
GARDEN.MID  Screenshot.png
wpshooter@JRO-ubuntu-3:~/DOWNLOAD$ kmid GARDEN.MID
KMid 2.0 Copyright (C) 1997,98,99,2000,01 Antonio Larrosa Jimenez. Malaga (Spain)
KMid comes with ABSOLUTELY NO WARRANTY; for details view file COPYING
This is free software, and you are welcome to redistribute it
under certain conditions

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
wpshooter@JRO-ubuntu-3:~/DOWNLOAD$

---

### Post by christhemonkey on 2006-08-20
I take it you have sound working for everything else?

---

### Post by wpshooter on 2006-08-20
Yes, sound works fine for wav files, system sounds and plays music CD just great.  Have never been able to get midi files to play on any of the 4 computers on which I have Ubuntu Dapper Drake 6.06 installed.  3 of these have built-in sound and the 4th the one I am trying now has a 5.1 live sound blaster card.

Is playing the midi files something that they have not fixed yet.  All of the post that I have read seems to indicate that most people to this point have not been able to get this to work.

Thanks.

---

### Post by christhemonkey on 2006-08-20
I havie always been able to play midi files fine, just need to load the snd-seq module.

```
aplaymidi -l 
```
Should give you a port, say 20:0, so you can do this:
```
aplaymidi -p 20:0 /bla/a/file/file.mid 
```
and you should be able to hear it fine.

---

### Post by wpshooter on 2006-08-20
I get this:

wpshooter@JRO-ubuntu-3:~$ aplaymidi -l
 Port    Client name                      Port name
 62:0    Midi Through                     Midi Through Port-0
wpshooter@JRO-ubuntu-3:~$ aplaymidi -p 62:0 /bla/a/file/file.mid
Cannot open /bla/a/file/file.mid - No such file or directory

---

### Post by christhemonkey on 2006-08-20
I meant replace /bla/a/file/file.mid with a real midi file and path.

---

### Post by wpshooter on 2006-08-21
Still no sound, just goes to a blank line on the terminal and sets there.

Have to hit X on diagonal to exit terminal.

---

### Post by christhemonkey on 2006-08-22
You can type CTRL+C to kill it at anytime.

Im not sure i can help you any further.
To play with a .mid with a GUI is not something that i have ever wanted to do.
If i want to play a .mid, i would normally play it with timidity in a terminal.
Or with the midi out onto my keyboard...

---

