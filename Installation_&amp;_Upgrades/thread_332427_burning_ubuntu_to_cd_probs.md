---
title: "burning ubuntu to cd probs"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by naphelge on 2007-01-06
i have downloaded ubuntu-6.10*desktop*iso 2 times now & tried to write to cdrom 4 times & everytime the cd rom keeps hanging up.

not sure what the prob is as i don't see any other posts here with any similar type probs. i know the cd rom burner is good... actually i have use 2 different laptops. 

when i d/load the ubuntu install image it is in *.iso format already so i just right click on the image i d/loaded & chose to write to disc with a blank 700MB cd rom in the writer.

i have verified the md5sum image i download from the internet & everything is koshur. however if i do an md5sum on the cd after it is burned i get a result that doesn't match anything on the ubuntu hashes page. 

i have never really had to try md5sum on burned cd roms before so i am not sure if this indicates a prob or not.

anyone have any ideas? i have a new laptop i want to try ubuntu on but i am getting close to going with FC6. but who needs two laptops running the same flavour of linux?

---

### Post by meng on 2007-01-06
It doesn't make any sense to md5sum the burned disc. Your burned disc should not contain an iso, it should contain a complete filesystem. Have a look and check that there are files and folders on there. If there is an iso on there, you haven't burned it properly. When you say the cd-rom hangs up, what do you mean by that?
[www.psychocats.net/ubuntu/iso](www.psychocats.net/ubuntu/iso)

---

### Post by Joeb on 2007-01-06
I am assuming you are burning the CD while in Windows, based on your description that you just right click on the file and tell it to write to the CD.  Assuming that is correct, if you do a directory of the CD or look at it under My Computer, do you see the .iso file or a bunch of files listed?

If just the .iso file then you aren't burning it correctly.  The .iso is an image of the disk and what you are doing is copying that image file to the CD (which is not what you want).

Do you have actual CD burning software installed?  If you do, it should have an option to create the cd from the image file.

---

### Post by naphelge on 2007-01-06
> It doesn't make any sense to md5sum the burned disc.
i agree it doesn't make sense... but after 4 burns i thought i would try.

i have looked at the contents of all the discs & they do appear to look like *complete* file systems. they compare identical also (2 of them anyhew).

> When you say the cd-rom hangs up, what do you mean by that?
when i try to boot from the disc i go to an ubuntu screen which looks good & i can get help if i click on F1 i think & change the language... but when i try to test the cd (to check for corruption)  or try to just go ahead with the default install i get the same screen with a *LOADING* across the top & it never changes. after about a 15-30 mins (with no indication of anything happening) i assume the disc is a bust.

i have also tried booting the cd's in another laptop (running FC6) & i get to the same ubuntu screen with the green *LOADING* after i try to check the cd where nothing happens except the cd rom stays busy.

i know the cdrom drives on the two laptops i am burning the cd on as well as the new laptop i am trying to install ubuntu on, all work fine. i have tried booting with mandrake10 & FC6 cd's & they boot fine.

so i am trying to burn disc #5. perhaps i have a bad batch of writeable cd's? that's what i am starting to think after 2 downloads (from different mirrors) with md5sum checks that look good burning 4 times.

---

### Post by naphelge on 2007-01-06
> I am assuming you are burning the CD while in Windows
running FC6 gnome. i right click the image from nautilus & there is a write to disc option that i have never had probs with writing to cd roms before. seeing this image has *.iso ext i assume it can be written direct to cd rom without making it an iso... hehe that sounds funny.

> Do you have actual CD burning software installed? If you do, it should have an option to create the cd from the image file.
i burn discs all the time this way nps with both laptops. i have been d/loading FCore since like 2 i think & burning my cd's ok nps. 

so i don't have any other computers to try & burn discs on & have d/loaded from different mirrors where the md5sum checks are good. it's gotta be bad writable cd roms i guess.

---

### Post by Joeb on 2007-01-06
Have you tried setting your burn speed down to  say 2x or 4x?  I think gnome will default to the fast speed it thinks it can get away with and maybe the media can't actually handle it.

---

### Post by naphelge on 2007-01-06
kk looks like i should have looked harder because another thread just got bumped with 6.10 install probs. looks like i should try the alternate ubuntu flavour.

d/loading now so i hope that worx. will post again how it turns out.

---

### Post by naphelge on 2007-01-06
> Have you tried setting your burn speed down to say 2x or 4x? I think gnome will default to the fast speed it thinks it can get away with and maybe the media can't actually handle it.

last burn disc #5 i set the burn rate to the lowest listed... i think it was like 9x (dunno why i didn't see a 2x or 4x but thinking about it now yeah the lowest listed was 9x). the discs are 1-48x speed discs.

however i have never used these discs before so i am not sure how good they are. looks like crap to me but i will know almost for sure after trying the alternate image if i get the same result.

---

### Post by naphelge on 2007-01-06
well i know the cd's i am burning to seem to a-ok. just burned an entire disc full of pictures & a second one full of mp3's. 

so i am just burning the altenate image & i hope that worx.

---

### Post by Joeb on 2007-01-06
> **naphelge said:**
> well i know the cd's i am burning to seem to a-ok. just burned an entire disc full of pictures & a second one full of mp3's. 

so i am just burning the altenate image & i hope that worx.

That's not necessarily true.  If you drop a random byte or two in a jpg or mp3, you won't notice it, however, if it's in an executable it will most likely cause a seg fault.  However, it is quite possible that it is an issue with the desktop cd and you hardware (did it boot into the live version?).  If so, the alternate cd should take care of it (and you now have a nice set of coasters for the next time you have company :)  )

---

### Post by bigken on 2007-01-06
yep sounds like a bad batch of media to me :-k

---

