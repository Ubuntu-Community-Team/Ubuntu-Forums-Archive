---
title: "Vista won't load correctly after 9.04 install"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by idontknowlinux on 2009-04-04
Problem: Vista won't load after I tried to dual boot 9.04
I just tried to boot the new 9.04 beta with both Vista and 8.04 already on my computer. I made it to where i needed to partition my hard drive (It was going to shrink Vista and add 10g's for 9.04). Then I got an error that it couldn't read the CD and that I should try burning it at a slower speed. I was going to try to burn it again so I went to Vista. When I tried using Vista it would go to the Vista boot screen, but after it was done I would see a black screen with just my mouse. It wouldn't even go to the Welcome Screen. I have already tried the windows recovery program to start from a recovery point but it said that there was an error with the C drive. I know my C drive is still in tact with all my Vista files because I used the 9.04 live CD to find my C Drive. All my files were still there and I even loaded one of my .odt files to make sure everything was working correctly. Someone in another thread had said to run a disk check, but he and I both don't know how to without being able to get onto windows. I'm taking ANY ideas that would get Vista up and running. 
FYI: Hardy Heron was dual booted onto Vista. It is a 32 bit.

---

### Post by psyke83 on 2009-04-04
Even though your C: drive may seem intact, it's quite possible that your filesystem is corrupt (especially if a partition was incorrectly resized). You need to use the System Recovery Options available from the Vista installation DVD.

See: [http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

I recommend you first attempt a Startup Repair, and if it does not work, open a Command Prompt via the System Recovery options, and run chkdsk.

For a "quick" check:
```
chkdsk C: /F
```

For an in-depth scan (may take a few hours):
```
chkdsk C: /R
```

Note: if you aborted the partition resize procedure, then chkdsk may not be capable of fixing all errors and recovering your files correctly.

---

### Post by idontknowlinux on 2009-04-04
I just tried the chkdsk C: /F and it worked :D. I can't believe that it was so simple :p. Thank you so much for fixing it.

---

