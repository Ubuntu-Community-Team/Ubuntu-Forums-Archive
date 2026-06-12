---
title: "Trying to boot live CD...."
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by gabriella on 2010-06-15
I decided I would try out Lucid 10-04. So I downloaded the ISO file direct from the Ubuntu site and burnt the image to a CD. I checked the MD5 hash before burning and it matched. 

Anyway it starts to boot gets as far as the "UBUNTU" bit with the moving dot underneath and doesn't progress any further. I get the impression the drive is constantly trying to read a track(s) off the CD. 

Has anyone else experienced this? Is it possible it could still be a bad download file even though the checksums hashes match? Just to be sure I stuck in the Karmic CD and that booted up fine. I've burnt three now all with the same results. Is it worth me trying a fresh download?

Any thoughts....?
Thanks

---

### Post by howefield on 2010-06-15
When booting, try pressing F6 after selecting your language, and select the nomodeset option. Then continue booting, if that doesn't work, press the Esc key after pressing F6 as above, and remove "quiet splash--" from the end of the boot line.

---

### Post by gabriella on 2010-06-15
> **howefield said:**
> When booting, try pressing F6 after selecting your language, and select the nomodeset option. Then continue booting, if that doesn't work, press the Esc key after pressing F6 as above, and remove "quiet splash--" from the end of the boot line.

I don't even get the language options at the beginning like on previous versions, just the UBUNTU logo on purple background. I suppose I have a bad CD? (all three of them) Which is weird since the MD5 hash's on the download file are OK.

---

### Post by irv on 2010-06-15
I had the same problem. The CD would boot in two other PC's but not in my old laptop. I just install 9.10 and let it go at that. I only use it for one thing anyway. I have it for the sound system at the chapel. and 9.10 is just find for that. 
I have been watching the install thread and others have had the same problem.

---

### Post by howefield on 2010-06-15
That's strange, the language setting and Try Ubuntu before installing ect options should be displayed in order to get "as far as the "UBUNTU" bit with the moving dot underneath"

Have you tried the CD in another computer ?

I also remember some posters who were able to boot from a pen drive where the CD failed.

---

### Post by gabriella on 2010-06-15
> **irv said:**
> I had the same problem. The CD would boot in two other PC's but not in my old laptop. I just install 9.10 and let it go at that. I only use it for one thing anyway. I have it for the sound system at the chapel. and 9.10 is just find for that. 
I have been watching the install thread and others have had the same problem.

Well I'm not alone then! thats some comfort I suppose!:rolleyes: Interesting I'm trying this on  a laptop. I'll have to try them in another machine tomorrow.

(nice part of the world you are in! I used to live in the twin cities)
G

---

### Post by gabriella on 2010-06-15
> **howefield said:**
> That's strange, the language setting and Try Ubuntu before installing ect options should be displayed in order to get "as far as the "UBUNTU" bit with the moving dot underneath"

Have you tried the CD in another computer ?

I also remember some posters who were able to boot from a pen drive where the CD failed.

Yes thats what I thought too. I was expecting that part right at the start like previous versions.
Will try another PC in the morning

---

### Post by gabriella on 2010-06-15
> **kansasnoob said:**
> Are you aware that the "boot options" menu is now hidden by default? When you first see the initial boot screen with two emblems "human = keyboard" you have about 3 seconds to press any key which will bring up the "select language" followed by the old boot options screen.

I'd begin by checking CD for defects and if it passes exploring some of the boot options under F6:

[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

Well I tried the CD's on another machine with the same result so figured they were bad and trashed them. Now searching around I find this above quote. Have I been an idiot and wasting my time? and everyone else's? That said this is the first I've heard about this and assumed the boot up would be the same as previous releases!

---

### Post by howefield on 2010-06-15
> **gabriella said:**
> Have I been an idiot and wasting my time? and everyone else's? That said this is the first I've heard about this and assumed the boot up would be the same as previous releases!

No, you haven't been an idiot, the quote is correct. 10.04 boot sequence is different than previous versions. Sorry, it didn't occur to me to ask earlier that you might have missed that change, I should have been more alert when you said you missed the language and options screen.

---

### Post by gabriella on 2010-06-15
> **howefield said:**
> No, you haven't been an idiot, the quote is correct. 10.04 boot sequence is different than previous versions. Sorry, it didn't occur to me to ask earlier that you might have missed that change, I should have been more alert when you said you missed the language and options screen.

LOL well I learn! But I'm glad to have found that since I was wondering how to test the burn side of my cd drive. I did notice the keyboard=human logo at the bottom and wondered what the point of it was!

---

### Post by irv on 2010-06-15
> **gabriella said:**
> Well I'm not alone then! thats some comfort I suppose!:rolleyes: Interesting I'm trying this on  a laptop. I'll have to try them in another machine tomorrow.

(nice part of the world you are in! I used to live in the twin cities)
G

I guess we all learn something today. I didn't know about the first screen and hitting a key either. 
and yes I am about 85 miles south of the twin cities right on the banks of the Mississippi river. I look at the river out my front window and in the morning I sit outside and watch the lazy river flow by. Just beautiful.

---

