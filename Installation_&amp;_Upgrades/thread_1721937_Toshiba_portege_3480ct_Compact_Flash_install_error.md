---
title: "Toshiba portege 3480ct Compact Flash install error"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by petebarchetta on 2011-04-05
Hello all,

I'm trying to install hardy on a portege 3480. I have connected via USB caddy and run it via a lynx build desktop and installed hardy via unetbootin onto the 8gb CF. the machine then boots to the menu where you chan choose live, memtest etc. on choosing the live option to boot the machine up it then bombs out with a error.
" menu.c32: not a com32R image
Boot:"

it gets this far, so its not far off, but i'm stumped as where to go next

any ideas guys. I'd love to get linux on this machine. i have read that tftpd is a possibility to get this running but have run into issues setting it up hence looking at removing the CF out for a unetbootin style install.

cheers

---

### Post by Dutch70 on 2011-04-05
Support for 8.04 ends this month. You really shouldn't install anything other than 10.04 or 10.10. 
[[COLOR="Red"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")

If you must install 8.04, when you get to the screen you described above, type "live" without the quotes & hit enter.
Security updates will stop this sometime this month.

---

### Post by petebarchetta on 2011-04-05
error.
" menu.c32: not a com32R image
Boot:"
 
The error keeps cycling around and it gives no clues as to what it needs,
Hitting tab brings up the uberbootin prompt but doesn't help any further as after a few seconds it repeats the error

---

### Post by Dutch70 on 2011-04-05
So, what happens when you type in "live" and hit enter???

if it doesn't work, try typing in "help" and hit enter.

---

### Post by petebarchetta on 2011-04-06
They say a picture paints a thousand words....[http://www.flickr.com/photos/8356136@N08/5595128235]("http://www.flickr.com/photos/8356136@N08/5595128235")

---

### Post by Dutch70 on 2011-04-06
> **petebarchetta said:**
> They say a picture paints a thousand words....[http://www.flickr.com/photos/8356136@N08/5595128235]("http://www.flickr.com/photos/8356136@N08/5595128235")

Forgive me if I'm wrong, but what that picture says to me is...

"I have not tried typing in "live" even though you've advised me to twice"

Is your keyboard not working, or have you really not tried it?

Here's my picture...:)

---

### Post by petebarchetta on 2011-04-06
It's not even looking like a busybox shell, its almost before that at grub as it's a boot prompt.
Im not very familiar with the limited boot prompt commands so any help would be good to rescue this build.

Thanks all

Apologies wrong image, it comes back with prompt "
[http://www.flickr.com/photos/8356136@N08/5595643359]("http://www.flickr.com/photos/8356136@N08/5595643359")

---

### Post by Dutch70 on 2011-04-06
You should try typing it in before you hit whatever you hit to bring up the unetbootin thing, but I'm not sure. I've never had any problems after typing in live, and I do it every time I boot one of my usb sticks.

Btw, you can use the paper clip in the toolbar of your post, to attach pictures. No need to put them on a website.

---

### Post by petebarchetta on 2011-04-06
typing help at the boot: prompt doesnt give anything apart from the same reply back "could not find the kernel image: help"

or any other command such as start, boot etc

so using the tab or not gives the same response back fromt he command line

this is what i'm stuck at. as its expecting something but gives no options, hence bringing it to the forum

---

### Post by Dutch70 on 2011-04-06
Yes, I have encountered that screen many, many times, on several different computers. I know that screen all too well. 
Typing "live" has not failed me once, this is the first time I've seen it not work. 
So, that's all I've got, sorry it didn't work for you.
Maybe someone else will have another idea.

---

### Post by petebarchetta on 2011-04-06
> **Dutch70 said:**
> Yes, I have encountered that screen many, many times, on several different computers. I know that screen all too well. 
Typing "live" has not failed me once, this is the first time I've seen it not work. 
So, that's all I've got, sorry it didn't work for you.
Maybe someone else will have another idea.

the only curveball is this is the first time i've run a CF card based install on a laptop. every other laptop build has been conventional rotating platter media and they have always worked even if they had to be chucked into the donor machine to build them. ( for some unknown reason i choose the difficult ones, either no pxe boot or  very problematic machines :P ) i know on the forum people say about the DMA / udma on the cf-ide convertors are an issue. so will look into that.

---

### Post by petebarchetta on 2012-08-25
Hello all.
I succeeded in getting the machine's OS on by slinging the HD in another donor machine, a tecra m3, once built swapped the drive back in and now have 10.04 running on the 3480ct
Still looking at the cf card issue, maybe down to the IDE to cf adaptor

---

### Post by overdrank on 2012-08-25
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

