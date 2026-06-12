---
title: "Can't even install Ubuntu 10.10 (or any other version or distro)"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by smg_0000 on 2010-12-07
I'm using 3 monitors over a pci-e 9800GT and an agp 7600GS and have no problems under Windows 7, except i can't have Ubuntu (which i really miss).

I tried installing Ubuntu and pretty much every other distribution multiple times.. with no luck so far. Wubi, CD, USB.. none of them worked for me. Right before the first step in the installation, all the screens go haywire, displaying all kinds of shapes and colors and everything seems frozen.

None of this ever happened back when i only had 2 screens and i really need the 3rd one (actually thinking of a 4th since i got a slot left.. maybe for movies or stuff while i'm working).

I found topics of people with similar problems, only they were reffering to whatever happens while inside ubuntu or whatever. Do any of you guys have an idea how i could work around this? Thanks.

---

### Post by tommcd on 2010-12-07
> **smg_0000 said:**
> 
I'm using 3 monitors over a pci-e 9800GT and an agp 7600GS and have no problems under Windows 7, except i can't have Ubuntu (which i really miss).
I tried installing Ubuntu and pretty much every other distribution multiple times. I tried installing Ubuntu and pretty much every other distribution multiple times.. with no luck so far. 
Why don't you try to simplify things. The fact that no linux distro will install implies that either:
1. You have hardware that no linux distro will support, or:
2. (More likely) You are doing something wrong.
Try installing Ubuntu with just one monitor attached. You can always add the other monitors later.

How are you using both an AGP and a PCI-E graphics card? Perhaps if you posted your hardware specs (lspci) and your graphics card(s), you could get some help with this.

And welcome to the Ubuntu forums!

---

### Post by smg_0000 on 2010-12-08
Well, thanks for your reply, i really gotta try installing again with the side screens unplugged (yes, i do have a strong tendency to complicate things and miss the essential).

I can use a PCI-E card and an AGP one at the same time because:
- the mobo has slots
- the nVidia driver for the 9800GT also supports the 7600GS so there's no conflict

Right now i'm teasing myself with a VirtualBox installation so a lspci output would be irrelevant, but i will try to provide the details manually:
- mobo : Asrock 4CoreDual-SATA2
- cpu      : Intel E5200 DualCore @ ~2.5 GHz
- ram : 2 x 2GB DDRII @ 800MHz
- gpu 1 : nVidia 9800GT
- gpu 2 : nVidia 7600GS

I hope i didn't leave out anything important and i apologize if i did but i haven't had any sleep in over 30 hours + i've been doing that a lot lately and it all just builds up... I'll come back with impressions on the upcoming install after i do something about my sleep pattern. Thanks again.

---

### Post by tommcd on 2010-12-08
I would try and see if you can install Ubuntu with just the PCI-E 9800GT and see if that makes a difference. You can always add the AGP card later.

---

### Post by ronparent on 2010-12-08
I had a problem with a recent ATI card where I couldn't install with two monitors plugged in. The display would remain blank with the generic driver. It ended up I could install with only one monitor connected and then replug the other monitor after the proprietary driver was installed! You might try a similar work aroundto see if it works for you.

---

### Post by smg_0000 on 2010-12-09
This is gonna be fun.. and also boring to just read (imagine how i felt actually going through all that). I tried the following things:
1. completely removed the agp card (FAILED) (didn't expect that)
2. unplugged the 2nd display from the PCI-E (FAILED)
3. thought the usb boot thingy was plotting against me, burned a cd and went back to step (1) in reverse order (FAILED)
4. remembered that windows 7 disabled my power icon in the systray some while ago AND interestingly enough, when the power goes out, my ups only holds for ~10 sec - figured it must have been the ups. unplugged the ups and went AC (FAILED)
5. remembered i had a problem once (can't remember any details of its nature) and unplugging my usb gamepad solved it - i unplugged the gamepad AND the second keyboard (yes i really use two of them) (FAILED)
6. booted to winxp and tried a wubi install under windows ...

Now this part got messy so <snip> the list above, i'm going narrative:

Can't say that wubi failed... it definitely did something. It added a new entry to my loader so now i had:
- Windows Xp
- Windows 7
- Ubuntu.

Like any other noob, i tried selecting Ubuntu and it gave me the infamous over-debated missing <really can't remember the filename> error (status 0xc00000f).

Under the Windows Xp tab i had two more tabs:
- Windows Xp
- Ubuntu.

Under Ubuntu i had 3 more tabs:
- Ubuntu <long string of <snip> that i can't remember>
- Ubuntu <same long string> (recovery mode <or console.. not sure>)
- Windows 7 (loader)

I thought the first option sounded reasonable enough so i went for it. (FAILED)
Went through the whole boot menu again and selected Ubuntu (recovery mode) - which worked like a charm and seemed to jump-start the whole system. The installation was on now and i was at last happy. When the installation was over, i restarted and hoped that Ubuntu would run w/o the recovery console <snip>. (FAILED)

I restarted, and went directly into recovery mode when a small blue window popped in the center of the screen with a new set of options i never seen before in my life (no wonder). FailsafeX just sounded right at that time so i went for it... with high hopes and a mad blunt in my mouth i was waiting for something to happen.. anything. Suddenly the screen went orange/yellow/brown/magenta (default wallpaper) and i was finally able to logon. I installed the updates, restarted, it was all still cool, i installed the nvidia driver, restarted and i was already thinking that it's finally working.. low graphics but it's working and i was ready to live with that.. ... at this point i shouldn't need to tell you i was never able to boot up to Ubuntu again.. so anyway if you had the patience to read through all this, you deserve a knock-knock joke. So... knock-knock! Who's there? <snip>

I almost forgot, here's what i mean, what the screen looks like when i say (FAILED).. (check the attachment). Not even sure it's worth mentioning at all, but that pattern was the same throughout over 20 boot failures - and the only thing different about it (and not visible in the photo) was a bunch of sporadic small dots colored in red, green and blue (if that's supposed to be some sick subliminal message, it wasn't subtle at all). I'm kinda down about all this and am thinking of giving up but would still desperately read any opinions you might have... what happened is simply way over my level of understanding (and that <snip> me.. in a moronic kinda way).

SWEET HOLY MOTHER OF SNIP! that bot cut out my knock-knock joke :( ... if that was foul it should hear me talk normally..

---

### Post by smg_0000 on 2010-12-09
sincerely sorry for this but DEAR GOD THAT'S A LONG POST!

---

### Post by ronparent on 2010-12-09
I don't see that you tried booting the live cd with the 'nomodest' parameter yet. It is extremely frustration but some systems just have to have some quirk that prevents booting until they are searched down and vanquished.

Edit: Problems with the display are far too common so there are additional boot parameters available depending on the make of you graphics chip set.

---

### Post by dino99 on 2010-12-09
you can follow this example to install 3 monitors

[http://ubuntuforums.org/showpost.php?p=9604915&postcount=2](http://ubuntuforums.org/showpost.php?p=9604915&postcount=2)

---

### Post by smg_0000 on 2010-12-13
Sorry for the late post.. i just finally got a bit of time so i decided to push forward and this is what i got so far:

@ronparent: you're a life saver.. i didn't even know about nomodeset cause i never had any problems but what doesn't kill ya makes ya stronger so i gotta thank you

@dino99: i read through the example and it seems pretty thorough and easy to understand.. i'm sure it will come in real handy when i get to solve the next problem i ran into:

So, yeah... i managed to install Ubuntu 10.10 eventually (and i thank all of your for your help) .. but now everytime i try to boot into it, i get dropped to the infamous BusyBox shell.

Before anything, i need to state that i've done pretty much nothing about it yet, but found some threads that seem to somewhat cover that. Now, for the sake of keeping this forum as clean as possible, i leave it up to you / a moderator whether we close this topic right now and tag it [SOLVED] (still can't believe it was all just hinging on a simple param) OR we dedicate it to the greater good - me having a stable fully working install ;)

---

### Post by tommcd on 2010-12-13
> **smg_0000 said:**
> 
So, yeah... i managed to install Ubuntu 10.10 eventually (and i thank all of your for your help) .. but now everytime i try to boot into it, i get dropped to the infamous BusyBox shell.

If *nomodeset* allowed you to install Ubuntu, then try booting with nomodeset added to the kernel line in Ubuntu.
When grub loads hit the "e" key to edit the entry to boot Ubuntu. Then scroll down to the **linux** line and remove the words *quiet* and *splash*. Then put *nomodeset* in where quiet and splash used to be.
Then hit **ctrl X** to boot. This will allow you to boot with nomodeset; and removing quiet and splash will allow you to see what is going on as the system boots.
This will only affect the current boot and will not make any permanent changes to the way Ubuntu boots.
Then try installing the nvidia driver from the Ubuntu repos and see if you can then boot to the desktop with the nvidia driver installed.

---

### Post by smg_0000 on 2010-12-14
It seems to be unable to reach /dev/sda6 - which where i had my installation at..
I checked /dev and there really isn't any sda6 ... closest two matches would be sda and sda1 (both zero bytes in size).
Should i try to re-install?

---

### Post by tommcd on 2010-12-14
> **smg_0000 said:**
> It seems to be unable to reach /dev/sda6 - which where i had my installation at..
I checked /dev and there really isn't any sda6 ... closest two matches would be sda and sda1 (both zero bytes in size).
Should i try to re-install?
What partition did you install Ubuntu to? How many partitions did you make for the Ubuntu install?
Try booting from the Ubuntu live CD and post here the output of: ```
sudo fdisk -l
``` 
Also, try running the *bootinfo script* from the live CD and post the output here.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 I am not very adept at interpreting the bootinfo script. I do know basically how it works though. 
Anyway, a lot of people on this forum are skilled at interpreting the bootinfo script so you should be able to get help with this.

---

### Post by smg_0000 on 2010-12-22
[FONT=Arial][SIZE=2]IT WORKS! i followed your advices and read through other people's posts and finally got it working as i always wanted to. I'm so happy i could format my windows partitions.. (which i almost lost in the process).

Basically i formatted the partition then, and installed again.. checked everything carefully with the advanced partitioning tool and failed.. turned out that everything was working out just fine with the nomodeset param but the updates i was getting after (possibly) altered the kernel and ruined the entire installation (i tried many nerd workarounds with no luck).

I ended up with two separate versions of the installation, out of which the old one works (seems to have all the updates installed though).. I even managed to easily configure all the 3 displays to work flawlessly. I thank everyone for their contribution, i hereby declare myself another happy ubuntu user.
[/SIZE][/FONT]

---

