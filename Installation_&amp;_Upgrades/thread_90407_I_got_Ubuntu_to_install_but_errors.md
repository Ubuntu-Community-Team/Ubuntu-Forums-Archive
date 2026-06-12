---
title: "I got Ubuntu to install but errors"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by newuser111 on 2005-11-14
ubuntu installed fine on a 20gb ext3 partition with a 1gb swap and the grub loader also works

but as soon as it boots into ubuntu, errors occur

"Buffer error on device sdf logical block 0"

"sdf : assuming drive cache write through"

these errors just cycle endlessly, until the system is rebooted, it doesnt boot into the x gui, it says there is a problem, trying to login in also makes no difference, and the screen is scrolled by the endless error messages

what could be wrong?  The integrity check for the CD showed it had no errors

---

### Post by Kapre on 2005-11-14
[QUOTE=newuser111]ubuntu installed fine on a 20gb ext3 partition with a 1gb swap and the grub loader also works

but as soon as it boots into ubuntu, errors occur

"Buffer error on device sdf logical block 0"

"sdf : assuming drive cache write through"

these errors just cycle endlessly, until the system is rebooted, it doesnt boot into the x gui, it says there is a problem, trying to login in also makes no difference, and the screen is scrolled by the endless error messages

what could be wrong?  The integrity check for the CD showed it had no errors[/QUOTE]

This also happened to me. Same style of problem. I dont know what to do so I just re-installed. I know that this is a pain in the #%^ but I got it from a bad d/l (yes even though the integrity check passed). I d/l another ISO and burned it on a slower speed. Also, it might be good to turn off the pc for about 20 mins and install again.

K

---

### Post by newuser111 on 2005-11-14
did you compare the MD5 checksums of the downloaded isos?

---

### Post by newuser111 on 2005-11-14
i just redownloaded and compared md5 value of the iso to the one listed in the download section, it is identical so the file cannot be corrupt

i will try burning it at the lowest speed

---

### Post by newuser111 on 2005-11-15
same problem using new cd

---

### Post by newuser111 on 2005-11-15
any recommendations?

---

### Post by XXFCTEXX on 2005-11-15
[QUOTE=newuser111]any recommendations?[/QUOTE]

Burn it at a slower speed, I think the standard is 8 and my older drives would not read anything burned that fast correctly. Set the burn speed at 4 and it worked great.

Try a different mirror, the ISO might be a bad file.

---

### Post by newuser111 on 2005-11-15
[QUOTE=XXFCTEXX]Burn it at a slower speed, I think the standard is 8 and my older drives would not read anything burned that fast correctly. Set the burn speed at 4 and it worked great.

Try a different mirror, the ISO might be a bad file.[/QUOTE]


the md5 value is as listed in the download section, it is not a bad file

and i burned at the slowest speed available (4x) i have a hard time believing there is anything wrong with the CD

---

### Post by newuser111 on 2005-11-16
well im using knoppix now instead of ubuntu, and i even installed it to the partition

it seems to be working great, too bad i couldnt get ubuntu to work

---

