---
title: "Realtek HD Drivers"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by c0ca1n3_boy on 2010-01-26
Hello guys, 

I installed ubuntu yesterday and I am new to linux.
Everything seems to work fine exept my audio card (Realtek).

There are official drivers in their site but I don't know how to install them.

Can somebody explain me the process.

Thanks!

:)

---

### Post by hemimaniac on 2010-01-26
The linux audio drivers come as a package from their site, once downloaded you need to extract them to a working folder then look at the README files in each one, between that and the install notes it will lay it out for you. From what i have seen in forums here and other sound related forums is that it has a 50/50 shot of working, seems alot of peeps are going on about the sound/audio problems in 9.10 across the board. Personally (imho) i would replace the 9.10 install with 8.10 or 9.04. Has a better chance of getting you sorted.

I also came across [this]("http://ubuntuforums.org/showthread.php?t=843012") afterword

---

### Post by hhlp on 2010-01-26
download the driver from realtek page and read the readme :

sometimes you have to use before unpacking :

[PHP]./configure
./make
sudo ./make install[/PHP]

---

### Post by c0ca1n3_boy on 2010-01-26
The problem is that their readme file is totaly wrong! I read it couple of times but still didn't get it.

However I've looked at the forums and I found this 

> **How I Installed Realtek sound drivers in 3 steps** 			 			 			 		   		 		 		I just built a new Ubuntu machine. The sound did not work. I searched these forums, the solutions gave me a headache. Isn't Ubuntu supposed to be easy to configure? I tried the easiest solution first, from the posts from aktiwers, and it really was simple. It took only 3 steps! The hard part was getting through all the verbiage.
 Here's how I did it( I'm repeating info from aktiwers, only to make it clearer and simpler and in 1 place):

What I didn't do: I did not download or recompile the latest ALSA. Why bother? It turns out I didn't need to do that, why hassle with it if you don't have to.

**Step 1:** Applications->Accessories->Terminal.  At the prompt paste in:
cat /proc/asound/card0/codec#* | grep Codec
it'll return something like, Codec: Realtek ALC888

**Step 2**: Go to [http://www.mjmwired.net/kernel/Docum...figuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt")
Find your Codec. There is a list of model name and descriptions for each Codec starting on line number785. Copy the model name you've got. For me it was 6stack-dig.

**Step 3:** Again at the terminal type sudo gedit /etc/modprobe.d/alsa-base
Provide pw when prompted.  Add at the end of file: options snd-hda-intel model=6stack-dig
Of course with your model in place of 6stack-dig.  Save the file.  That's it!

It helped me. I posted here in case somebody have the same problem.

Regards :)

---

