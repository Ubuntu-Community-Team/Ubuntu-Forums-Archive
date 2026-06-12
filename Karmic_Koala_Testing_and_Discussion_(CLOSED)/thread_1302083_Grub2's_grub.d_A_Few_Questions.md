---
title: "Grub2's grub.d: A Few Questions"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Penguin Guy on 2009-10-26
The default scripts in /etc/grub.d/ contain a few methods that I'm slightly confused about. I'd be grateful if some experienced Linux user could answer my questions below. Note: The codes are not actually PHP (they are Sh), I just put them in the PHP boxes for the pretty syntax-highlighting ;).

1) What is the best way to add a separator to Grub 2, my method doesn't seem to work:
[PHP]menuentry "----------" {}[/PHP]

ANSWER: If the menuentry starts with a '-', it is treated as an argument, to fix this, simply add a space before the first '-': [PHP]menuentry " ----------" {}[/PHP] ([http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8590250](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8590250))





2) Why not replace this:
[PHP]
prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/update-grub_lib
[/PHP]
With this:
[PHP]
. /usr/lib/grub/update-grub_lib
[/PHP]

ANSWER: 'Semantics'






3) WTF is going on here?:
[PHP]
test_numeric ()
{
	local a=$1
	local cmp=$2
	local b=$3
	if [ "$a" = "$b" ] ; then
		case $cmp in
			ge|eq|le) return 0 ;;
			gt|lt) return 1 ;;
		esac
	fi
	if [ "$cmp" = "lt" ] ; then
		c=$a
		a=$b
		b=$c
	fi
	if (echo $a ; echo $b) | sort -n | head -n 1 | grep -qx $b ; then
		return 0
	else
	return 1
	fi
}
[/PHP]

ANSWER: 'Semantics'

---

### Post by kansasnoob on 2009-10-26
I'd suggest looking here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by drs305 on 2009-10-26
If you look at a lot of the config files it seems apparent they were written by different people with different styles. Some like "sed", others don't. I imagine the answer to your questions would just be "because that's the way I wrote it!"...  ;-)

I don't really cover any of that in the file linked above, although the "Grub 2 Title Tweaks" comes a bit closer for the geeks out there. [http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602") My guess is you could tidy up a lot of those tweaks and add a lot of your own.

---

### Post by Penguin Guy on 2009-10-27
> **drs305 said:**
> If you look at a lot of the config files it seems apparent they were written by different people with different styles. Some like "sed", others don't. I imagine the answer to your questions would just be "because that's the way I wrote it!"...  ;-)

Why would somebody write their own if function? Either I'm missing something, or the Ubuntu dev's don't have a clue what they're doing.

---

### Post by drs305 on 2009-10-27
> **Penguin Guy said:**
> Why would somebody write their own if function? Either I'm missing something, or the Ubuntu dev's don't have a clue what they're doing.

The chances of me explaining not clearly explaining it or you missing something are vastly greater than the chances the devs don't have a clue. I am sure it was the way that I explained it.  ;-)

The scripts are all there for viewing in /etc/grub.d

---

### Post by VMC on 2009-10-27
> **Penguin Guy said:**
> Why would somebody write their own if function? Either I'm missing something, or the Ubuntu dev's don't have a clue what they're doing.

Have you tried replacing those PHP codes with your own? If so, how did they work out?

---

### Post by dino99 on 2009-10-27
> **VMC said:**
> Have you tried replacing those PHP codes with your own? If so, how did they work out?

yeah,

as you feel, experiment your coding, test and let us know if its better.

Anyway, grub2 only can be improved  :D

---

### Post by Penguin Guy on 2009-10-27
> **drs305 said:**
> The scripts are all there for viewing in /etc/grub.d
> **VMC said:**
> Have you tried replacing those PHP codes with your own? If so, how did they work out?

Yeah, checked through all the scripts, including /etc/default/grub /usr/lib/grub/update-grub_lib. Couldn't see any uses of test_numeric, so deleted it. I also changed everything above to my way of doing things, ran update-grub2, and everything works fine (but with less code :p). Also all the code above is actually shell code, not PHP code.

---

