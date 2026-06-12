---
title: "I mess up my flash player..."
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by chris1neji on 2010-03-16
Okey i am a new user.
yesterday all i did was go to a website and firefox said i needed plugins and such and my flash player was working. Went to youtube and i could see videos =D.
But i came upon a problem which if i click anywhere in youtube it didnt respond i could only pause and play videos by pressing spacebar. This was very anoying try going back to the beggining of a video just because u wanted to go back a few seconds. So i search and i found this [http://sites.google.com/site/alucidfs/how-i-do/clicking-in-flash-not-working](http://sites.google.com/site/alucidfs/how-i-do/clicking-in-flash-not-working)
that fixed it. wohoo i was happy. Today later on i downloaded a few things that my friend said would probably make it easier on me was Ubuntu Tweak. Anyways i was messing around with a few things. Now i go to youtube it didnt work. 

Step by step instructions please. half the time i use that command prompt it doesnt work -_-.
I feel very computer illiterate on a Linux OS.
Running Linux something koala 64bit

---

### Post by tommcd on 2010-03-16
> **chris1neji said:**
> Okey i am a new user.
yesterday all i did was go to a website and firefox said i needed plugins and such and my flash player was working. Went to youtube and i could see videos =D.
What "plugins" did you download?
For future reference, it is usually NOT a good idea to just download any "plugins" that some website says you need. Unless you explicitly know and trust what they are giving you, this is good way to get malware on your computer. Since you are using linux and not Windows, you are unlikely to be infected with anything; but you should still be cautious and follow good security practices.
> **chris1neji said:**
> 
 Today later on i downloaded a few things that my friend said would probably make it easier on me was Ubuntu Tweak. Anyways i was messing around with a few things. Now i go to youtube it didnt work. 
Exactly what things were you "messing around with"?? And how did you mess with them? You should be specific with things like this. It helps to troubleshoot.
 It is generally not a good idea to mess with stuff unless you know exactly what you are messing with. More importantly, always make sure you have an exit plan. That is, always be sure you can undo what you have done in case something gets screwed up.
> **chris1neji said:**
> 
Step by step instructions please. half the time i use that command prompt it doesnt work -_-.
I feel very computer illiterate on a Linux OS.
Running Linux something koala 64bit
Now for (hopefully) a fix.
First try uninstalling and reinstalling flash. To uninstall:
```
sudo apt-get remove --purge flashplugin-installer
```
Then rename the .macromedia directory in your home directory:
```
mv ~/.macromedia ~/.macromedia.bak
```
Then reinstall flash:
```
sudo apt-get install flashplugin-installer
```
Now start Firefox and go to you-tube and see if flash works properly.
If this does not work, you will have to describe exactly what you did that caused this problem. That is what exactly did you get from Ubuntu Tweak? And what did you do with it?
Hope this helps.

---

### Post by legendb on 2010-03-16
64 bit Koala, sounds like you have the common flash bug. Try setting your preferences for visual settings to basic.

---

### Post by chris1neji on 2010-03-16
thanks ill try this later today. I did trust the site as i have always used it before and its very popular among people. 
 
What i mess with was my "flash" i believe it told me i was outdated o.0 or something like that i believe that was my cause of problem. But i did mess with a few other things which i cant remember to this very moment but i dont believe they would have cause a conflict with flash.
My exit plan was to remove and reinstall which i did and it didnt work either. Maybe i was not doing it correctly. My plan C exit was to load windows and continue working and take a break and went back to reading :D

---

### Post by tommcd on 2010-03-17
> **chris1neji said:**
> 
My exit plan was to remove and reinstall which i did and it didnt work either. Maybe i was not doing it correctly. My plan C exit was to load windows and continue working and take a break and went back to reading :D
Did you uninstall and reinstall flash as I said in my last post? If so, then did you get any errors? And did you rename the ~/.macromedia directory after uninstalling flash as I posted?

Did make any changes to your system after going to Ubuntu Tweak?

And what exactly happens when you try to play videos on You Tube?

---

