---
title: "Text to speech voices for Ubuntu 20.04.2 LTS"
date: 2021-06-20
forum: Installation &amp; Upgrades
---

### Post by thebishoppear on 2021-06-20
I made a mistake in another thread which apparently caused it to be closed. I mistyped the Ubuntu version I have. So, to be exact, it is Ubuntu 20.04.2 LTS. Let me restate the situation. Please read through without instantly rejecting the possibility, because it does work to some capacity at Lichess.org

I will explain now.

ORIGINAL POST: 

**"Hello, I am trying to get text to speech voices for Ubuntu 12.04 [COLOR=#ff0000][mistake: I should have typed 20.04.2][/COLOR]. Specifically, I am trying to get it to announce chess moves. One link which works with Firefox installs espeak with the following command:**

**"sudo pacman -S speech-dispatcher espeak"**

**However, this only works in Firefox, not Chromium (and I haven't tested Opera yet). The voice is very hard to understand and I would like to get more natural sounding voices. One site has what appears to be what I am looking for but maybe it has been discontinued as I can't get it to work. It is Gespeaker. Does anyone know about this? [http://www.muflone.com/gespeaker/english/download#tabs](http://www.muflone.com/gespeaker/english/download#tabs)**

[B]If I am correct about it not being supported, then does someone know of another way I can get this to work?"

[/B]
In that thread it was stated that it was difficult to achieve, and a few areas of possibilities were listed. The speech dispatcher command above does work. It does give low quality computer voice announcements of moves. The only thing is that there are no additional voices.

So, with the Ubuntu version correction and noting again that at least one avenue has worked, I would like to ask the question again.

Is there a way to get more natural human sounding voices to work? An improvement on the speech dispatcher for espeak perhaps? Even if it is pay only, I would like to see the options to get this done. Announcing chess moves is very important to me.

Thank you for your time. Please allow me time for follow up questions after you reply instead of closing the thread.

---

### Post by Holger_Gehrke on 2021-06-20
"sudo pacman -S speech-dispatcher espeak" should have returned an error along the lines of 'command not found' or started a game of Pac-Man. The package manager of that name is part of Arch but not of Ubuntu. But since both espeak and speech-dispatcher are AFAIK part of the default install this doesn't matter at all.

Gespeaker used to be available from the repositories in Version 0.86 (which is the current release) but isn't anymore as of Ubuntu 20.04; not surprising since it's been out for 5 years and there's been no new release since then; on github it looks like a major rewrite with a tag of "2.0" is underway but nothing has been officially released.

But Gespeaker is just a graphical frontend for espeak and mbrola. It might make the installation of additional voices easier and give you a graphical interface for typing in text for it to speak, but to make other software 'speak' you're still going to go through speech-dispatcher. 'speech-dispatcher' itself is not a speech synthesizer. It's a server that waits for programs to send it text to speak and then processes that text and passes it to the actual synthesizers. If speech-dispatcher is correctly installed, you should have configuration files for it in /etc/speech-dispatcher/. The syntax for these files is described in an info-file included with speech-dispatcher. If you've got the info-reader installed you can enter 'info speech-dispatcher' on the command line and read that documentation. Through those files you can configure which speech synthesizer and what voice you want to use.

Holger

---

### Post by thebishoppear on 2021-06-20
**"But Gespeaker is just a graphical frontend for espeak and mbrola."**


That just is a major asset to non-programmers. We are pilots and not engineers. We know how to fly planes, but we don't know how to tighten the gears.


We need GUI. Microsoft doesn't need to have a monopoly on this.




**"'speech-dispatcher' itself is not a speech synthesizer. It's a server that waits for programs to send it text to speak and then processes that text and passes it to the actual synthesizers"**


Couldn't get 1 male and 1 female to say the letters "A" to "H" and numbers "1" to "8"?


Then just words like "to" (a2 to a4) or "short"/"long" with "castle" (to get "short castle" or "long castle"), and then the simple ones "check", "checkmate", and "takes".


I would be willing to do it for free for the male side, and if you like falsetto voice I could try the female version.




You just reference the computer and not some server or anything. Why is it that we assign thumps and thud sounds when a chess piece is moved or a file is selected, but we can't do that in this case? I am still not understanding the dilemma. It just seems like some copyright issue. How is this not possible to achieve?




**"If speech-dispatcher is correctly installed, you should have configuration files for it in /etc/speech-dispatcher/. The syntax for these files is described in an info-file included with speech-dispatcher. If you've got the info-reader installed you can enter 'info speech-dispatcher' on the command line and read that documentation. Through those files you can configure which speech synthesizer and what voice you want to use."**


I don't know what any of that means. I am sure it means something to a programmer, but how can we get Linux to people who don't do computer talk? Do they have to resort back to Windows? 


You have a user friendly GUI, you click a male or female voice that sounds natural and you use that as a default. If you want other voices, you pay. It seems like a doable solution. 


Did you know that they even took Roger Ebert's video reviews and found a way for him to talk without his actual voice functioning?


[https://youtu.be/_0KUw3xr7cA]("http://youtu.be/_0KUw3xr7cA")


Have a listen. Surely, one of you programmers out there can do something and not make us inferiors resort to terminal "sudo sumo" wrestling moves.

---

### Post by sudodus on 2021-06-20
I have been using (and tweaking) espeak, but mainly for Swedish. Anyway, I could find some English male and female voices by looking into the voices directory of espeak,

```

sudo apt install espeak   # checked in 20.04.2 LTS

guru@ssds:/usr/lib/x86_64-linux-gnu/espeak-data/voices$ ls -l
totalt 52
drwxr-xr-x 2 root root 4096 jun 20 22:24  asia
-rw-r--r-- 1 root root   38 mar 22  2020  de
-rw-r--r-- 1 root root   38 mar 22  2020  default
-rw-r--r-- 1 root root  110 mar 22  2020  en
-rw-r--r-- 1 root root  264 mar 22  2020  en-us
-rw-r--r-- 1 root root  181 mar 22  2020  es-la
drwxr-xr-x 2 root root 4096 jun 20 22:24  europe
-rw-r--r-- 1 root root   82 mar 22  2020  fr
drwxr-xr-x 2 root root 4096 jun 20 22:24  mb
drwxr-xr-x 2 root root 4096 jun 20 22:24  other
-rw-r--r-- 1 root root  106 mar 22  2020  pt
drwxr-xr-x 2 root root 4096 jun 20 22:24  test
drwxr-xr-x 2 root root 4096 jun 20 22:24 '!v'
guru@ssds:/usr/lib/x86_64-linux-gnu/espeak-data/voices$ ls -l '!v'
totalt 76
-rw-r--r-- 1 root root  93 mar 22  2020 croak
[COLOR="#FF0000"]-rw-r--r-- 1 root root 324 mar 22  2020 f1
-rw-r--r-- 1 root root 357 mar 22  2020 f2
-rw-r--r-- 1 root root 375 mar 22  2020 f3
-rw-r--r-- 1 root root 350 mar 22  2020 f4
-rw-r--r-- 1 root root 425 mar 22  2020 f5[/COLOR]
-rw-r--r-- 1 root root  38 mar 22  2020 klatt
-rw-r--r-- 1 root root  38 mar 22  2020 klatt2
-rw-r--r-- 1 root root  39 mar 22  2020 klatt3
-rw-r--r-- 1 root root  39 mar 22  2020 klatt4
[COLOR="#0000CD"]-rw-r--r-- 1 root root 335 mar 22  2020 m1
-rw-r--r-- 1 root root 264 mar 22  2020 m2
-rw-r--r-- 1 root root 300 mar 22  2020 m3
-rw-r--r-- 1 root root 290 mar 22  2020 m4
-rw-r--r-- 1 root root 262 mar 22  2020 m5
-rw-r--r-- 1 root root 188 mar 22  2020 m6
-rw-r--r-- 1 root root 254 mar 22  2020 m7[/COLOR]
-rw-r--r-- 1 root root 186 mar 22  2020 whisper
-rw-r--r-- 1 root root 392 mar 22  2020 whisperf

```

You can test the 'f' (female) and 'm' (male) voices. I hope you find some voice that works well for you, for example

```

espeak -v f3 "Hello world"
espeak -v m3 "Hello world"

```

---

### Post by Holger_Gehrke on 2021-06-20
> **"But Gespeaker is just a graphical frontend for espeak and mbrola."**
That just is a major asset to non-programmers. We are pilots and not engineers. We know how to fly planes, but we don't know how to tighten the gears.
We need GUI. Microsoft doesn't need to have a monopoly on this.

You misunderstood what I meant by "graphical frontend". Since I'm still  on 18.04 I installed gespeaker and it's basically a text entry field and  a play button. Press the button and it speaks the text you entered. You  can make some settings (which of the installed synthesizers to use,  what voice to use, speed and pitch control and even gives you a list of  voices it knows about and tells you whether or not they are installed)  but it can't configure speech dispatcher or any of the synthesizers and  it can't install either synthesizers or voices. It's basically the  graphical equivalent of the command line tool 'spd-say'. Not helpful at  all if you're trying to get some other program to speak.

> 
**"'speech-dispatcher' itself is not a speech synthesizer. It's a server that waits for programs to send it text to speak and then processes that text and passes it to the actual synthesizers"**
Couldn't get 1 male and 1 female to say the letters "A" to "H" and numbers "1" to "8"?

Then just words like "to" (a2 to a4) or "short"/"long" with "castle" (to get "short castle" or "long castle"), and then the simple ones "check", "checkmate", and "takes".
I would be willing to do it for free for the male side, and if you like falsetto voice I could try the female version.

You just reference the computer and not some server or anything. Why is it that we assign thumps and thud sounds when a chess piece is moved or a file is selected, but we can't do that in this case? I am still not understanding the dilemma. It just seems like some copyright issue. How is this not possible to achieve?


A 'server' means a program that offers a service to other programs, either locally or across a network. speech-dispatcher was written as a unified interface for programs that want to output speech. Using speech-dispatcher a programmer doesn't need to know what synthesizer(s) are installed or what voices it can do, the program just gives the text to speech-dispatcher. A program can ask speech-dispatcher about synthesizers, voices, available audio output system and so on and tell it what to use and doesn't have to bother with all the details of how to do these things.

Speech synthesis is something very different from just playing samples of speech. The text gets transformed into a list of phonemes (a phoneme is the smallest unit of speech which can change the meaning of an utterance) then those get transformed into sound samples and played. To stay with your example, the sounds for the letters 'A' to 'H' and the numbers '1' to '8' are different between different languages. Playing sampled speech we'd need to either do it in only one language or have hundreds of sound files for localization. When using speech synthesis we only need to translate the text (far less data) and the synthesizer takes care of speaking it correctly.

> 
**"If speech-dispatcher is correctly installed, you should have configuration files for it in /etc/speech-dispatcher/. The syntax for these files is described in an info-file included with speech-dispatcher. If you've got the info-reader installed you can enter 'info speech-dispatcher' on the command line and read that documentation. Through those files you can configure which speech synthesizer and what voice you want to use."**

I don't know what any of that means. I am sure it means something to a programmer, but how can we get Linux to people who don't do computer talk? Do they have to resort back to Windows? 

You have a user friendly GUI, you click a male or female voice that sounds natural and you use that as a default. If you want other voices, you pay. It seems like a doable solution. 


Editing configuration files is not programming. It's just writing out option names and values in the simplest case (yes, there are programs whose configuration is more complicated than that; it's still just configuration). For servers like speech-dispatcher that are used by other programs and not directly by the user a GUI for configuration would add hundreds or even thousands of lines of code; since it's basically set-it-and-forget-it that would be a colossal waste of time.

And speech in Chromium doesn't work because chromium is Google Chrome without all the stuff that relies on Google online services. Chrome implements the Webspeech Application Programming Interface by sending the text to a google server that sends backs a sound file with the speech which then gets played. Firefox on the other hand simply connects to speech-dispatcher on Linux (and to the MS Speech Synthesizer on Windows).

Holger

---

### Post by de Bacon on 2022-03-15
I intend no offense here, that is in no way my desire. However, I do believe that those answering this post simply don't get it! I think this because those saying it are unlikely to actually need or rely upon the type of functionality that gespeaker implements. This is not some sort of game, it is a powerful tool to those of us whom find great difficulty in reading. I need a program like gespeaker that functions with a large degree of ease.  Why re-invent the wheel?  Gespeaker is a wonderful program.  I depended on it for years then, poof gone with the update to 20.04.  Speech Dispatcher may work with someone whom understands programming, but to the lay person, like myself it does nothing. Open a terminal, enter its command, it says okay I'm running, that's all folks.  I am quite sure that the person whom initiated this thread is in agreement with how speech-dispatcher functions.

Personally, I am now forced to use Orca, a totally cumbersome process.  It works in ways, although; now apparently it has lost its former setup and options, so is more a cumbersome distraction to what I attempt to do,  than being a true benefit in assisting with a degree of fluidity.  It is a nightmare to use, when it is speaking documents, it can't be paused in the middle of some long piece.  If it stops the user must either find where it stopped, (the last word spoken) a chore in itself, highlite the remainder, only then will it continue speaking or, the user must then begin again listening to that which had been spoken previously, before it continues.  With long documents that can be a grand waste of time, to say nothing of the frustration such situations create.  Again I say why re-invent the wheel.  GeSpeaker is a wonderful resource and would benefit many, were it enabled to function within a modern Ubuntu system.
  
Thanks for reading, if you did, please see about making the old wheel work once again.  Its code is intact somewhere.

---

