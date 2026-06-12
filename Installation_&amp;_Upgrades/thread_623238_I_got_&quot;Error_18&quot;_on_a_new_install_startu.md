---
title: "I got &quot;Error 18&quot; on a new install startup"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by mylarjorgen on 2007-11-25
I downloaded ubuntu-7.10-desktop-i386.iso to my WindowsXP 866

tested it on winMd5Sum fine

Burned it to CDROM, first two tries failed then I set it to burn at 4X, burned and tested fine with its own integrity test on the front screen.

So far, so good.

then i clicked install and got two lines saying 

[ 234.284559] Buffer I/O error on device f 60. logical block 0
[ 272.376782] Buffer I/O error on device f 60. logical block 0

(I filmed it loading and im not quite certain that is a 6 in "f 60" as the clarity of film is quite poor, but i can email the clip if you need it.)
my email is [email]mylarjorgen@yahoo.com[/email])

then it continued 

 *Setting preliminary keymap...

then some other things

then someting about REBOOT failing

then some other stuff and what looked like another problem to me

then when it finished is said something about no errors and everything being OK but when i rebooted, it loaded the HDD, CDROM and DVD, blacked as normal the came back on with the wessage

GRUB Loading stage1.5


GRUB Loading. please wait...
Error 18
_


then nothing more.

Sorry if i seem a bit unclear but i dont really know what i was looking at.

Any ideas folks?


I don't know the solution, but I do admire the problem.

---

### Post by oldos2er on 2007-11-25
How old is your computer? You may need to update your BIOS.

---

### Post by mylarjorgen on 2007-11-25
Thanks for the reply,

Not really sure, it seems to be powered by steam. heh.

It's a PIII 866 but thats all i know. I would guess about 5 years maybe???

How would i find that out?

I looked in Device Manager> Processors> Details> Device Instance ID and it says its a FAMILY_6_MODEL_8\_0 and i did see a few driver dates that were 01 but im not sure, it was 2nd hand.

If it is the BIOS, how would i update it?

Will i need to convert it to electricity? heh.

[email]Mylarjorgen@yahoo.com[/email]
-------------------------------------------------------------------------------------
I dont know the answer, but i admire the problem.

---

### Post by jmedina on 2007-11-25
That is the same error I got when I used the Live CD. I would recommend you trying the alternate CD.

---

### Post by Tacuabe on 2007-11-25
I've just received the disks with version 7.10.

So far, I've had two problems. The first one (and quite a nuisance) is that upon shutdown and a new
restart I get a message "Grub loading please wait..." and then "Error 18". After that, nothing else
happens and the only solution is to switch off the machine. 

A stop-gap solution I found is starting Ubuntu from the installation CD, restart the computer,
remove the CD and follow the normal sequence. Ubuntu will work correctly and all my previous
settings (I have a separate /home partition) are still there. I even reinstalled some software
without any difficulties. As you can imagine this is both unusual and baffling.

This error, already reported above is happening with a year old machine, a Pentium IV, 2.8 Ghz and 1 Gb RAM. So the solution suggested by oldos2er wouldn't apply.

The second problem is the printer. My Canon Pixma iP1200 is not working anymore. I can't even
print a test page. I searched for a suitable driver with the printing utility but there is none
for my specific model. I did test several Canon printer options just in case. No luck.

Any suggestions folks? Thanks in advance!

---

### Post by mylarjorgen on 2007-11-25
> **jmedina said:**
> That is the same error I got when I used the Live CD. I would recommend you trying the alternate CD.

Hi, Im a total newbie, am i right in thinking the live CD is the one i downloaded and burned and the alternate is the one you send off for?

You really need to talk in "retard" terms or i wont understand. heh.

but thanks for the reply.

---

### Post by mylarjorgen on 2007-11-25
Hi Tacuabe, Regarding this quote from your last reply; 

A stop-gap solution I found is starting Ubuntu from the installation CD, restart the computer,
remove the CD and follow the normal sequence. Ubuntu will work correctly and all my previous
settings (I have a separate /home partition) are still there. I even reinstalled some software
without any difficulties. As you can imagine this is both unusual and baffling.
---------------------------------------------------------------------------------

I must be really, really dumb but i dont think i followed that.
I start the PC with the downloaded CD, yes?
Then I restart my computer?  so I boot it twice?

When it has booted up, I take out the CD, ok. but follow the mormal sequence.?????     sequence of what? installation or just running the software?   if its installation, how can I install without the CD in? if its using it from the CD, the same question applies.

Is this a stop-gap for "your" problem? If so, it would have been nice if you had mentioned that. it reads as though you are offering me a solution to my problem. It just serves to make me even more unsure about the whole thing.

---

### Post by Tacuabe on 2007-11-26
Hi mylarjorgen,

Sorry to have confused you even more. Perhaps I shoulda been more specific, the idea was to convey that I am experimenting the **same** error you're reporting. The "solution" is far from that, it only enables me to run Ubuntu 7.10, period. But it's quite a hassle and far from ideal, that's why I dubbed it stop-gap.

Let's make things clear. I _did_ _not_ download Gutsy Gibbon, I ordered the disk from Canonical. It's a Live CD and yes, I have heard of an "alternate" CD but don't know what it is or where/how you get it.

I stumbled on the "solution" when I got Error 18 upon my first boot _after_ _installation_. In desperation I booted once more from the Live CD and took a look at /boot/grub/menu.lst but did not find anything unusual there. I shutdown the computer and removed the Live CD from the tray. Decided to give it another try and started the machine _without_ the CD and...presto! my grub appeared and I was able to start 7.10 without any further problem.

The above was tested several times and it works, but as said, is far from being a solution. You may want to check [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18) which contains a detailed explanation of what is really happening. There's a real solution explained too, but I'm afraid my knowledge is no better than yours and I am aware that messing with partitions and the MBR is dangerous.

I have maintained WXP for personal reasons and I can't afford to lose some data and programs still present there. I will try to find help on how to proceed safely. If I do find a way, rest assured I will post it ASAP. Perhaps somebody out there can lend a hand to both of us.

---

### Post by mylarjorgen on 2007-11-27
Hi Tacuabe, Thanks for clearing that up and the thing about a "live CD". Thought i was being *really* dumb for a minute  there.

---

### Post by oldos2er on 2007-11-28
>> If it is the BIOS, how would i update it?<<

 Go to your BIOS manufacturer's web site, download an update, apply it. If you need more help, you can find it by Googling 'bios updating faq'.

---

