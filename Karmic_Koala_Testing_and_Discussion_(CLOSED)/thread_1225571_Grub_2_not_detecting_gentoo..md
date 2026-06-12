---
title: "Grub 2 not detecting gentoo."
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by durand on 2009-07-28
Hi,

Grub 2 doesn't seem to be detecting my gentoo install. When a kernel update comes out, I see that os-prober finds gentoo but for some reason, it isn't added to my boot menu. Any ideas?

Thanks!

---

### Post by ranch hand on 2009-07-28
Where are these 2 installations?  By this I mean are they on the same drive or separate drives?

---

### Post by durand on 2009-07-28
Both on the same drive. I've only got one drive. I should probably say that I also have sabayon (which is based on gentoo) installed and that does not get detected either.

---

### Post by ranch hand on 2009-07-28
I will have to get back to this thread later.  I am on my test drive right now and don't have my 9.10 and grub2 bookmarks even though I am on 9.10.

I am having some problem with Mandriva.  Grub2 picks it up and lists it but will not boot (not found error).

I think from something I read earlier that our problems may be related.

Sabayon is one I have tried and really did not like the results.  It wouldn't boot after I installed on only 2 partitions (/ and /home).  It seemed to want more.  I wasn't amused enough to screw with it.  9.10A3 is installed on those partitions now.

---

### Post by durand on 2009-07-29
I installed it with just a root partition and it works fine if I manually add it to grub.cfg..

---

### Post by Darkshade on 2009-07-29
I guess I shouldn't complain that my grub detects my 2nd karmic install twice then :lolflag:

---

### Post by durand on 2009-07-29
That would be the two separate kernels it detects, wouldn't it?

---

### Post by ranch hand on 2009-07-29
> **durand said:**
> That would be the two separate kernels it detects, wouldn't it?
I bet not.  I get a couple duplicates regularly, can't seem to get them to go away but they don't seem to hurt anything except make the menu longer.

---

### Post by ranch hand on 2009-07-29
> **durand said:**
> I installed it with just a root partition and it works fine if I manually add it to grub.cfg..
Well, I'll have another whack at it when 9.10 gets boring.  I have several different versions (different configurations and a mix of upgrades and clean installs, 64 and 32, etc.)

I probably should have had a little more patience but a distro that will install but not boot from its own grub (the other OS' did fine from that boot/root) just pissed me off so I just over wrote it.

grub.cfg is over written each time update-grub is run so that is a pain.  Check

[http://ubuntuforums.org/showthread.php?t=1223280](http://ubuntuforums.org/showthread.php?t=1223280)

These guys are starting to figure out how to write to grub2.  It will come and I believe it will be better than grub-legacy (which I just love).

---

### Post by ranch hand on 2009-07-29
[https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202](https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202)

[http://www.drlock.com/blog/2008/07/11/tweaking-grub-2/](http://www.drlock.com/blog/2008/07/11/tweaking-grub-2/)

I have not had time to really look these over but they may help.

---

### Post by durand on 2009-07-29
Thanks, I can manually add entries but it would be nice if grub automatically adds them. os-prober definitely sees gentoo so I have no idea why grub doesn't.

---

### Post by Darkshade on 2009-07-29
> **durand said:**
> That would be the two separate kernels it detects, wouldn't it?

Nope, check out the attachment.
The first 4 options are for my main install on my first hard disk. The next 4 are for my Kubuntu on my 2nd hard disk (yeah I know I gotta update it but I've been busy) and the last 4 are duplicates of the previous ones (same kernel).

p.s. Sorry for the crappy quality, made with a Nokia s40 cellphone.

---

### Post by durand on 2009-07-30
I noticed that I have the same problem with duplicate entries :S.

PS: Won't be posting here for 3 weeks cos I'm in canada :)

---

### Post by Darkshade on 2009-07-30
> **durand said:**
> I noticed that I have the same problem with duplicate entries :S.

PS: Won't be posting here for 3 weeks cos I'm in canada :)

Have fun there! ):P




... and get ready for lots of updates when you get back :D

---

### Post by ranch hand on 2009-07-30
We do let people post from Canada.

---

### Post by wayne_cat on 2009-07-30
> **ranch hand said:**
> We do let people post from Canada.

true ... but his questions must end with "eh?"

---

### Post by durand on 2009-08-21
Hi! Back from canada and not actually heard anyone end a sentence with eh? :P I'm going to try the links ranch hand posted and post back if I get anywhere with them.
Thanks.

---

### Post by durand on 2009-08-21
I followed the instructions on the ubuntu wiki and I got update-grub to add a custom entry. Here is what I did:

Replace lines in /etc/grub/40_custom with:
```
echo "Adding Gentoo" >&2
cat << EOF
menuentry "Gentoo" {
        set root=(hd0,9)
        linux /boot/gentoo root=/dev/sda9 ro
}
EOF

```

Make it executable.
```
sudo chmod +x /etc/grub/40_custom
```

Update grub
```
sudo update-grub
```

It should then boot gentoo correctly.

What I still want to know is why os-prober just throws away the gentoo and sabayon installs it detects.

---

### Post by ranch hand on 2009-08-21
I think it is still a work in progress.

It picks up my Mandriva installations but will not boot from anything generated in the grub.cfg file.

```

echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
EOF

```
I am glad you gave your entry that works.

As you can it is different from mine.

Interesting.

A few of us may be able to be of some assistance when the panic starts on release;
Oh My God WHAT HAPPENED TO THE MENU.LST FILE  HELP!!!!!!!!!!!

I think that there may be a bit of that.

Good thing they are putting this in now.  By the time Lusty Lemming comes out it may actually work on its own.

I think it is pretty neat and should be more flexible than grub-legacy.  That also had (I hear) a lot of theathing problems.

---

### Post by bennachie on 2009-08-21
Grub2 doesn't identify Linux Mint either, and the only solution appears to be to manually edit a file that you are allegedly not supposed to edit. "Work in progress" sounds like a reasonable description of the Grub2 project. Let's hope it gets fixed before 9.10 is officially released.

---

### Post by durand on 2009-08-21
I thought os-prober was an ubuntu script, not a grub2 one.

---

### Post by ranch hand on 2009-08-21
> **bennachie said:**
> Grub2 doesn't identify Linux Mint either, and the only solution appears to be to manually edit a file that you are allegedly not supposed to edit. "Work in progress" sounds like a reasonable description of the Grub2 project. Let's hope it gets fixed before 9.10 is officially released.
See above for how to create a file that holds up that will boot Mint.

Try both, you will have to edit to fit your partition, but you could but your version of both in a file (create 06_custom to put entries at top of menu) in /etc/grub.d.  Run update grub.  Reboot and give them both a try.

We would love to hear the results.

---

### Post by ranch hand on 2009-08-21
> **durand said:**
> I thought os-prober was an ubuntu script, not a grub2 one.
There seems to be a little difference (maybe it will work better) but it is part of the update-grub process with grub2.

All the files in /etc/grub.d (that are executable) run every time update grub is run to create the /boot/grub/grub.cfg file.  That file, which is completely over written each time update-grub is run, is the source of the menu you see.

You can, in 05_debian_theme set the background for your menu and the color of the menu font as well as the highlight font color.

---

### Post by dinxter on 2009-08-22
seems to be a problem in 30_os-prober with linux case, specifically linux-boot-prober return nothing but os-prober will return the expected details, ie, in 30_os-prober, line 68 with
```

LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"

```LINUXPROBED is empty so we get no boot entry. but if we replace linuc-boot-prober with

```

LINUXPROBED="`os-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"

```then LINUXPROBED is,
/dev/sdc3:Gentoo^Base^System^release^1.12.11.1:Gentoo:linux

so we get the right grub entry generated

i'm taking it its a linux-boot-prober script bug (from os-prober package) rather than a bug in 30_os-prober, but it can be 'fixed' by making the replacement above in 30_os-prober, though i dont know how that will effect other os detection.
correctly would be to fix the linux-boot-prober-script i'm guessing, can someone post the bug report this is filed on please, thanks

---

### Post by dinxter on 2009-08-22
something going wrong in /usr/lib/linux-boot-probes/mounted/90fallback i imagine

```
+ log debug: running /usr/lib/linux-boot-probes/mounted/90fallback on mounted /dev/sdc3
+ basename /usr/bin/linux-boot-prober
+ logger -t linux-boot-prober debug: running /usr/lib/linux-boot-probes/mounted/90fallback on mounted /dev/sdc3
+ /usr/lib/linux-boot-probes/mounted/90fallback /dev/sdc3 /dev/sdc3 /var/lib/os-prober/mount ext3
+ partition=/dev/sdc3
+ bootpart=/dev/sdc3
+ mpoint=/var/lib/os-prober/mount
+ type=ext3
+ mapdevfs /dev/sdc3
+ mappedpartition=/dev/sdc3
+ exitcode=1
+ echo /vmlinuz
+ grep -q boot/
+ kernbootpart=/dev/sdc3
+ eval ls /var/lib/os-prober/mount/vmlinuz
+ echo /vmlinux
+ grep -q boot/
+ kernbootpart=/dev/sdc3
+ eval ls /var/lib/os-prober/mount/vmlinux
+ echo /boot/vmlinuz
+ grep -q boot/
+ kernbootpart=/dev/sdc3
+ eval ls /var/lib/os-prober/mount/boot/vmlinuz
+ echo /boot/vmlinux
+ grep -q boot/
+ kernbootpart=/dev/sdc3
+ eval ls /var/lib/os-prober/mount/boot/vmlinux
+ echo /boot/vmlinuz*
+ grep -q boot/
+ kernbootpart=/dev/sdc3
+ eval ls /var/lib/os-prober/mount/boot/vmlinuz*
+ echo /boot/vmlinux*
+ grep -q boot/
+ kernbootpart=/dev/sdc3
+ eval ls /var/lib/os-prober/mount/boot/vmlinux*
+ echo /vmlinuz*
+ grep -q boot/
+ kernbootpart=/dev/sdc3
+ eval ls /var/lib/os-prober/mount/vmlinuz*
+ echo /vmlinux*
+ grep -q boot/
+ kernbootpart=/dev/sdc3
+ eval ls /var/lib/os-prober/mount/vmlinux*
+ exit 1
+ [ 0 = 1 ]
+ rm -rf /tmp/os-prober.tcyfOF
```

---

### Post by dinxter on 2009-08-22
doh, 90_fallback only looks for vmlinu[xz], it wont handle different kernel names automatically. easy enough to add a few more likely kernel names to 
for kernpat in /vmlinuz /vmlinux /boot/vmlinuz /boot/vmlinux "/boot/vmlinuz*" \
                "/boot/vmlinux*" "/vmlinuz*" "/vmlinux*";
but will it handle the seperate /boot partition, i'm not so sure

---

### Post by dinxter on 2009-08-22
it would fail on finding a matching initrd anyway,
initrdname=$(echo "$kernfile" | sed "s/vmlinu[zx]/initrd\*/")

---

### Post by dinxter on 2009-08-22
and ignore that replacing linux-boot-prober with os-prober in 30_os-prober nonsense i mentioned earlier, that wont help at all, on a more than superficial look for all the reasons above. os-prober cant handle autodetecting the gentoo case at the moment unless theres quite a lot of additional work done by linux-boot-prober, its manual grub.d script addition or nothing at the moment

---

### Post by dinxter on 2009-08-22
i can't actually see any sane way this could even be implemented as an auto-detection. the script process would effectively go
1. found a Gentoo base system on sdX
2. but the /boot could be anywhere so you'll need to tell me where
3. and i cant be sure of kernel names so if you could tell me those too
4. and the initrd names that match each kernel please
5. ok, i'll 'auto-generate' that for you now.

in essence detection cant be automated unless the case is relatively simple, more than that then it needs to be manual added

---

### Post by ranch hand on 2009-08-22
OK  You have me pretty lost here.

I admit to little abilities with scripts.  It is a short coming that I intend to work on but am a littoe short on time right now.

I have not used os-prober with grub-legacy much because I was never real happy with the results.  It was easier to build the menu (/boot/grub/menu.lst) from the menus of indevidual OS'.

Grub2 seems to be doing a good job of detecting most debian based OS' (with some weird querks).  Grub-legacy was using pretty much the same type of probe (I think) to detect other OS' and did so automatically and pretty reliably on installation of a new OS.

I do not understand how this can be done on installation and not be equally easily done at some other time.

---

### Post by dinxter on 2009-08-22
> I admit to little abilities with scripts.  It is a short coming that I intend to work on but am a littoe short on time right now.Trust me, that makes 2 of us! :)
> I do not understand how this can be done on installation and not be equally easily done at some other time.the amount of effort to write enough cases into os-prober beyond the simplest does seem like overkill, especially to generate 4 lines in a menuentry. a simple executable in grub.d to generate it manually is a great deal more simple

---

### Post by durand on 2009-08-22
I do understand what you're getting at. Gentoo doesn't have any strict naming scheme for kernels but usually, they are stored in /boot. Would there be a way to check all the files in there, and if it looks like a kernel, add it to the list? For me, I've only got one file called gentoo in there. Oh and I don't use initrd, apparently they aren't needed when everything is built in to your kernel.

BTW, Fedora's also detected properly so its not just debian systems.

---

### Post by dinxter on 2009-08-22
it possibly could be done, you could have os-prober make a guess at what looks like a kernel, it could then perhaps guess at the matching initrd and if it can't find one assume that it hasnt made a mistake and that it just needs that kernel. 
it could also try and guess that if the kernel's on it's own seperate /boot partition  that its meant to go with the base install on another partition that its found.
the amount of educated guesswork and code in detecting that kind of situation would be quite difficult to make sane i'd reckon, and i doubt it could be made even reasonably certain that the resulting menu entry is a valid one.
that much work for an unreliable stab at autodetecting an os just doesnt seem very justified to me. 
i could be wrong but it looks too unreliable and complicated to add to auto os generation.
bearing in mind that it is only 4 lines of meu entry its trying to add, it just seems far easier to leave the less obvious linux partitions to a manual grub.d script

---

### Post by durand on 2009-08-22
You do have a point but you would only need to write something like that once and it will support practically every linux distro. I have no idea how the current prober works though..

---

### Post by dinxter on 2009-08-22
> **durand said:**
> You do have a point but you would only need to write something like that once and it will support practically every linux distro. I have no idea how the current prober works though..
maybe someone could write it so that it works, its beyond me :) , it just seems that by design it would have to make so many assumptions that it wouldnt be very reliable and so not actually very useful. 
either that or it would need to ask a number of questions about the root partitions and the kernel image from the user to be reliable, which if they knew the answers to they would have just as well added it manually.
maybe theres some clever way to do it but i just cant see it

---

### Post by ranch hand on 2009-08-22
> **dinxter said:**
> it possibly could be done, you could have os-prober make a guess at what looks like a kernel, it could then perhaps guess at the matching initrd and if it can't find one assume that it hasnt made a mistake and that it just needs that kernel. 
it could also try and guess that if the kernel's on it's own seperate /boot partition  that its meant to go with the base install on another partition that its found.
the amount of educated guesswork and code in detecting that kind of situation would be quite difficult to make sane i'd reckon, and i doubt it could be made even reasonably certain that the resulting menu entry is a valid one.
that much work for an unreliable stab at autodetecting an os just doesnt seem very justified to me. 
i could be wrong but it looks too unreliable and complicated to add to auto os generation.
bearing in mind that it is only 4 lines of meu entry its trying to add, it just seems far easier to leave the less obvious linux partitions to a manual grub.d script
True.  My entries for Mandriva are only really 2 working lines;
```

menuentry "Mandriva" {
linux (hd0,14)/boot/vmlinuz
initrd (hd0,14)/boot/initrd.img
}

```
Just between the { }s.

---

