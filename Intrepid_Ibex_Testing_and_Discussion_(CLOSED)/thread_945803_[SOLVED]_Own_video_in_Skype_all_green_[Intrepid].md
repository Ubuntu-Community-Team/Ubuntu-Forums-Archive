---
title: "[SOLVED] Own video in Skype all green [Intrepid]"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rekado on 2008-10-12
Hi all,
I recently ran into problems with Skype's webcam support. It all worked well with Hardy, upgraded to Intrepid and the video was all green when testing it in the options of Skype or when turning it on for a call. It does (after the latest update) work in Cheese and it always worked in Ekiga (which is no option in my current network setting unfortunately).

Did anybody else run into problems with a noisy green video which seems to just be completely independent of what the webcam is pointed to? Attached is a screenshot. Just imagine the same green image but with the noise moving a bit around.

As I said, I installed all updates and the video works flawless in all other applications. It also should not be Skype as it worked in Hardy. Where can I start looking for the mistake...?

I assume it is a change to library that Skype accesses. Is there a list of libraries available that Skype uses for video support?

---

### Post by fballem on 2008-10-12
I have the exact same issue in Skype, but the camera does work in Cheese. The camera is a Logitech Communicate STX.

The Skype video was working in 8.04, but not in Intrepid Beta.

---

### Post by rekado on 2008-10-13
Think it's worth reporting as a bug? I'm not sure yet what package is responsible for that. The issue is locked down to Skype as it seems.

---

### Post by Toe on 2008-10-13
This is probably related to [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)
A lot of webcam stuff changed with the new kernel.

Installing the package libv4l-0 and starting Sype with the command "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" is a workaround that fixed the green noise from my Logitech cam.

---

### Post by rekado on 2008-10-13
Thanks for the hint. I will check it once I'm home in a few hours. (If it works then I'll click on the "Thanks" button...)

---

### Post by fballem on 2008-10-13
> **Toe said:**
> This is probably related to [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)
A lot of webcam stuff changed with the new kernel.

Installing the package libv4l-0 and starting Sype with the command "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" is a workaround that fixed the green noise from my Logitech cam.

I get an error when I try to execute (screenshot attached). I have verified that the v4l1compat.so exists and is in the specified folder.

Please advise

Thanks,

---

### Post by rekado on 2008-10-13
Is there a similar message when executing it from the terminal? Just guessing here...

---

### Post by Toe on 2008-10-13
I just tried it:
The command only works when executed from a terminal.

Hopefully Skype gets fixed soon and we don't need this workaround anymore.

---

### Post by fballem on 2008-10-13
> **rekado said:**
> Is there a similar message when executing it from the terminal? Just guessing here...

I get a number of errors, as shown on the attached screenshot.

---

### Post by rekado on 2008-10-13
These errors are unrelated to adding "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" in the call. I also noticed them yesterday when just executing skype from the terminal.
Does Skype start despite the error messages?

---

### Post by fballem on 2008-10-13
yes - but I don't know if it works - I use a Logitech headset for my calls.

---

### Post by rekado on 2008-10-13
Err, now I'm confused... You can test if video works in the options, can't you? And what is that to do with the headset?

Click the little blue button on the bottom left corner in the main Skype window and select "Options". Then go to video devices, select your camera and hit "Test". If you can see whatever the webcam is pointed to, well, then it works.

To test your headset you can just make a test call.

---

### Post by eldragon on 2008-10-30
in order to have a more easy life, ive created a file in /usr/local/bin called skype that superseeds the binary in /usr/bin/ which is in charge of running skype...

type
```

$ sudo gedit /usr/local/bin/skype

```

and paste the following 2 line
```

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```

then make it executable
```

$ sudo chmod a+x /usr/local/bin/skype

```

no more crazy command typing :D just run with the shortcut, or alt-f2 and type skype

---

