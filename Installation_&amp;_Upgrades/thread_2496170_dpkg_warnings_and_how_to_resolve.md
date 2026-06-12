---
title: "dpkg warnings and how to resolve?"
date: 2024-03-16
forum: Installation &amp; Upgrades
---

### Post by blahboybaz on 2024-03-16
When doing ```
$ sudo apt update $$ sudo apt upgrade -y
``` I get the following dpkg warnings ```
dpkg: warning: unable to delete old directory '/var/lib/ubuntu-advantage': Directory not empty
``` and ```
dpkg: warning: unable to delete old directory '/etc/ubuntu-advantage': Directory not empty
```. After googling about it I see instruction advising to ```
sudo rm -rf /var/lib/ubuntu-advantage/* && sudo rm -rf /etc/ubuntu-advantage/*
``` in order to resolve the issue.

Of course I would ```
sudo mv /var/lib/ubuntu-advantage /var/lib/ubuntu-advantage.backup && sudo mv /etc/ubuntu-advantage /etc/ubuntu-advantage.backup
``` and then remove that later if no problems arose.

But is ```
sudo rm -rf /var/lib/ubuntu-advantage/* && sudo rm -rf /etc/ubuntu-advantage/*
``` a safe course of action? And is it the only thing that should be done or should I also ```
sudo apt-get install --reinstall ubuntu-advantage
``` after that.

Maybe I shouldn't ```
sudo rm -rf /var/lib/ubuntu-advantage/* && sudo rm -rf /etc/ubuntu-advantage/*
``` at all bc it would break my system?

And what about dpkg?

If I did ```
sudo rm -rf /var/lib/ubuntu-advantage/* && sudo rm -rf /etc/ubuntu-advantage/*
``` is there some follow up dpkg command I should issue to fix any broken or unresolved issues with it?
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**tldr; **Basically I'm getting a dpkg warning about two directories that it can't remove because they have contents in them. I googled about it and found instruction telling me to manually force remove the directories but I'm not sure that is the safe or right thing to do. Also I'm not sure if I should reinstall the package associated with the directories (Ubuntu Advantage) in order to do a complete fix or if I should just not be removing those dirs at all. One final question is (if it is safe to remove the dirs and I do) is there some follow up command for dpkg or anything else that I should issue to resolve any conflicts or unresolved stuff?

I realize that because its just a warning it isn't critical to the operation of my system but I like to keep things clean and tidy so I really just want to fix this.

Thanks in advance for any help.

---

### Post by ajgreeny on 2024-03-16
That warning really is of no consequence at all and you can totally ignore it.
It is simply because a folder (directory) containing files can not be removed with a simple rm command when dealing wit package management.

---

### Post by blahboybaz on 2024-03-16
> **ajgreeny said:**
> That warning really is of no consequence at all and you can totally ignore it.
It is simply because a folder (directory) containing files can not be removed with a simple rm command when dealing wit package management.

[SIZE=2]I understand that and I even mentioned that myself in my op. I *want* to fix it - but I want to make sure I don't mess anything up in doing so.[/SIZE]

---

### Post by #&amp;thj^% on 2024-03-16
It really is just a silly thing, but that is the way the package manager works as a safety precaution to not over write an existing folder.

But is it safe, I'm still up in the air about that personally.
```
sudo rm -rf /var/lib/ubuntu-advantage/* && sudo rm -rf /etc/ubuntu-advantage/*


```
after that runs on mine:
```
ls  /var/lib/ubuntu-advantage
apt-esm  status.json

```
Now the important part:
```
ls  /etc/ubuntu-advantage
ls: cannot access '/etc/ubuntu-advantage': No such file or directory

```
This is the bad part:
```
sudo apt install ubuntu-advantage
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package ubuntu-advantage

```
I believe this is what you meant:
```
apt policy ubuntu-advantage-tools
ubuntu-advantage-tools:
  Installed: 31.1
  Candidate: 31.1
  Version table:
     31.2 100
        100 http://archive.ubuntu.com/ubuntu noble-proposed/main amd64 Packages
        100 http://archive.ubuntu.com/ubuntu noble-proposed/main i386 Packages
 *** 31.1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu noble/main i386 Packages
        100 /var/lib/dpkg/status

```
Back-ups are your best friend..
```
sudo mv /etc/ubuntu-advantage.backup /etc/ubuntu-advantage

```
```
ls /etc/ubuntu-advantage
uaclient.conf

```

I get where your heart is, but is it really worth the effort?

---

### Post by blahboybaz on 2024-03-17
> **1fallen said:**
> 
It really is just a silly thing, but that is the way the package manager works as a safety precaution to not over write an existing folder.
I get where your heart is, but is it really worth the effort?


Yes. As evidenced by the fact that I've spent this much effort to get some guidance.

Why do people argue with me about the validity of my desires? Don't we all have the right to care about whatever we care about? All I asked was for some guidance in resolving something I had already determined (for myself) was an issue worth addressing - not questioned about my reasoning or invalidated. If others wouldn't care about something like this then that's their prerogative.

> **1fallen said:**
> 
But is it safe, I'm still up in the air about that personally.


Thank you - that's slightly useful even if if isn't conclusive.

At the end of the day I'd still like to get help with this.

---

### Post by #&amp;thj^% on 2024-03-17
> **blahboybaz said:**
> Yes. As evidenced by the fact that I've spent this much effort to get some guidance.

Why do people argue with me about the validity of my desires? Don't we all have the right to care about whatever we care about? All I asked was for some guidance in resolving something I had already determined (for myself) was an issue worth addressing - not questioned about my reasoning or invalidated. If others wouldn't care about something like this then that's their prerogative.

No argument, as I said, it's just something personal....and I showed the outcome. And no one is stopping you from doing the same.

> **blahboybaz said:**
> 
Thank you - that's slightly useful even if if isn't conclusive.

At the end of the day I'd still like to get help with this.

I'll never say it's safe for everyone....sorry if that's not  conclusive enough.
```
aptitude why ubuntu-advantage-tools
i   xubuntu-desktop     Depends update-manager                   
i A update-manager      Depends update-manager-core (= 1:24.04.4)
i A update-manager-core Depends ubuntu-advantage-tools (>= 30~)  

```
Regards

---

### Post by MAFoElffen on 2024-03-17
@blahboybaz ---

Post #2 of ajgreeny was spot-on and should have been enough to accept. You took that further. 1fallen tried to explain and settle your fears.

You seem to be a bit defensive and read much between the lines that are not there. If I read between the lines of your posts, you seem to be offensive and agressive towards those that are honestly and sincerely trying to help you.

I am blatantly honest and call things as I see it. I truely hope that is not what you are consciously doing to the Members here. They are trying to help you. Accept their answers as that.

If not, then this Support Section is not the place to cause troubles. I am a bit protective of the Members here.

Going back to our question and Post #2's explanation... Stick arpund long enough and you will learn to just ignore that message type in the system updates. It is a harmless message that says it attempted to remove a directory, but because it was not empty, it left it there. No harm. No foul. No problem. Note that it did not throw an error on that at all. It was just an informative info type message. Not even a warning.

Play nice please. Live well.

---

### Post by blahboybaz on 2024-03-18
@1fallen  ):P

I'm real sorry man. I didn't read your [post]("https://ubuntuforums.org/showthread.php?t=2496170&p=14182660#post14182660") thoroughly and I should have done that before responding. I really appreciate you taking the time to share the info with me and I apologize for that mistake. I hope you can forgive me. I will mark this as solved.

---

### Post by ajgreeny on 2024-03-18
Nothing really to forgive, knowledge is always useful, and I'm slightly at fault in post #2 for saying it was a warning; it was not a warning at a&#314;l, as MAFoElffen said, but merely information.

---

