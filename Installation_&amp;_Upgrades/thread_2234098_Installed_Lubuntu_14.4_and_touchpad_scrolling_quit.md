---
title: "Installed Lubuntu 14.4 and touchpad scrolling quit working"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by JRinWV on 2014-07-12
I have an Acer Aspire 5750 laptop, 4 GB ram Intel i7-2630QM CPU @ 2 GHz x 8. I recently installed Lubuntu 14.04 LTS using a disk that came with the magazine Linux format. I also performed an update just the other day hoping that would solve the problem.

Now scrolling in general is hosed, the touchpad won't scroll using the right edge, as it has with every version ever installed. Also, the down arrow cursor key now causes the screen to move to the very bottom of the web page, rather than scrolling down gradually. The space bar still works as expected, scrolling down a full page.

Any advice would be appreciated!

---

### Post by sudodus on 2014-07-13
Welcome to the Ubuntu Forums :-)

Some examples of how it works for me in a terminal window (with Lubuntu 14.04 LTS)

- List a lot of things, for example a big text file (**cat filename**) or list a directory with enough files (**ls -l dirname**) to make the number of lines larger than the linux in the window. Then try scrolling with the mouse or touchpad. It works for me.

- Display a a big text file (**less filename**) to make the number of lines larger than the linux in the  window. Then scrolling with the mouse or touchpad does not work for me.

-o-

By the way, what version of Lubuntu is it? It might be old and past the end of life (EOL). Please check with the following command

```
lsb_release -a
```

If older than 14.04 LTS, I suggest that you download an iso file to install this current version of Lubuntu. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

---

### Post by Linuxour on 2014-07-13
I did the following on Ubnutu 14.04 
 System Settings --> Mouse & Touchpad 


and checked on "natural scrolling".

I hope it helps in Lubuntu 14.04

 You will find it different from other earlier versions - for example if you want to go down a page you have to scroll for up not down - unfortunately I don't know how to edit this. Good luck.

---

### Post by JRinWV on 2014-07-13
Hi Sudodus, I just did install 14.04 when this problem showed up, as I  mention in the fine print at the beginning of my cry for help... not so  interested in terminal windows compared to browser windows, but think it  should work the same way everywhere.  Thanks for responding!

Hi  Linuxour, w ent to Mouse & Touchpad, saw that natural scrolling was  checked, but so was something called two finger scrolling - no idea what  that is, but when I unchecked it, that fixed things. Don't believe I  didn't see that before as I have been there at least 2 or 3 times trying  to get it to work.

It does seem backwards, but I think I can get used to that pretty well.

Thanks for reminding me to check the settings and look at them with a fresh eye!!! Keep up the good work!

---

