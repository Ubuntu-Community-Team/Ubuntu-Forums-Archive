---
title: "Acer AL1716 monitor"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by eekfonky on 2007-11-07
I have just installed Gutsy and all is fine except there is a grey box floating around the screen saying "Input Not Supported" Am I perhaps missing a driver for the AL1716?
Please help it's driving me mad?

---

### Post by wonk-o-matic on 2007-11-08
You might have two video adapters, perhaps one on the motherboard and another in a slot.  Look for another video connector, and try that.

---

### Post by eekfonky on 2007-11-10
The one I'm using is on an NVIDIA Geforce FX 5200

---

### Post by Herman on 2007-11-10
Hello eekfonky,
What result do you get when you boot with the Ubuntu Live CD and try the command 'sudo ddcprobe'?
```
sudo ddcprobe
```
That should identify your monitor and give you a list of resolutions your monitor will support and some other things.
Otherwise, try to find out what resolutions your Acer AL1716 monitor should support, (from the owner's manual or manufacturer's website or where ever you can get that kind of info,

Then you should be able to mount your hard disk installed Ubuntu operating system in your Ubuntu Live CD and access your etc/X11/xorg.conf file by following the example in this link: [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000].

Your etc/X11/xorg.conf file is the file you need to edit to try to set the right resolutions in Ubuntu for your display and keyboard and mouse settings as well.

I had the same problem with my Acer AL2014W when I installed Feisty Fawn, and solved it by simply pasting the right resolutions into the 'mode lines' in etc/X11/xorg.conf. 
I am luckier with Gutsy Gibbon, I didn't have to do anything special, Gutsy got it right for me with all my computers. 

Here is a link to another thread with an example in it so you can see what I am talking about, [/COLOR][/COLOR]                                                                                                             [Help with screen resoultion]("http://ubuntuforums.org/showthread.php?t=505249")
 As you will see it works for some but not for others. Fortunately it works for me at least.

Try that and good luck, I hope you will be able to solve your problem easily like I did. Don't be shy to post here again with any questions if you aren't sure of something and I'll try to explain things better for you.
Regards, Herman :)

---

### Post by louieb on 2007-11-10
I've got the fx5200 and an Acer al1916w. I've see that gray box a few time too. The fix for me has been to choose resolutions where the refresh rate is at 60 kHz and below. As long as I do that the vesa, nv and the restricted drivers all work.

---

### Post by eekfonky on 2007-11-11
I used synaptic and downloaded the "915" for the Intel chipset. It had the correct resolution and refresh rate there. Problem solved.

Thanks for the help

---

