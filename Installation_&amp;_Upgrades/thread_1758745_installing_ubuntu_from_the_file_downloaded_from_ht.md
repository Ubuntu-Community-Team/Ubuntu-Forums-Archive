---
title: "installing ubuntu from the file downloaded from http://www.ubuntu.com/download/ubuntu"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by rahil_evi on 2011-05-15
i have downloaded ubuntu from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) this web site.The download consists of files pool,pressed,isolinux and so on.
but the instructions page says that we need to write the iso image to a cd .
i am unable to find the iso image.pls help me with the installation process.
the current operating system running on my computer is windows 7 .
regards
rahil

---

### Post by wojox on 2011-05-15
When you open that page look at step 1. and press the big orange button Start Download.

---

### Post by mikewhatever on 2011-05-15
The file you download is the .iso image that you have to save to disk. Looks like you've unpacked the image with an archive manager. Don't do it.

---

### Post by pablopancho on 2011-05-15
The file you downloaded is an .iso file. Don't open it, just burn it on a cd using e.g. ImgBurn (you can get this program at [http://www.imgburn.com/](http://www.imgburn.com/) and install it on Windows 7) or any other burning software. Try burning it on low speed.

---

### Post by rahil_evi on 2011-05-15
hi all thank you very much 
i have downloaded it using internet download manager.it was downloaded as a zip file .
and so i have extracted it.there comes the problem i am unable to find the iso file .
thanks again 
waiting for help 
rahil

---

### Post by timothy48342 on 2011-05-15
I'd bet that whatever program you use to open zip files (and other  archives  including .iso's) is set to automatically open the archive  instead of offering the choise to open it or save it. When I click that  big orangeish "download" box a window comes up that asks if I want to  open it with a specific program, or save it. It also asks if I want to  "do this automatically for files like this from now on." (using  firefox) For you apparently it is already automatically opening it  instead of offering options.

If that is what is happening the correct fix would probably be to get  that option reset in your browser. (No clue how to do that) Normally you  could right-click and select "save link" but it seems they disabled the  right-click menu.

Some possible workarrounds:
Find where the file is stored. For me in firefox a download list come up  and I can right-click and then select "open containing folder". In  WinXP it is "C:\Documents and Settings\MYUSERNAME\My  Documents\Downloads"
If you can find where the download is actuallty stored, go there and see if there is an .iso file called:
ubuntu-11.04-desktop-i386.iso
or
ubuntu-11.04-desktop-amd64.iso
If it is there, then that's what you need to burn.

Otherwise I found a direct download directory. It is like an ftp page, but it has a lot of files in it. 
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/11.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/11.04/release/)
Each is a clickable link, but it is hard to tell which is the right one. someone else may know. 
I don't see any file that EXACTLY matched either of the 2 that can come  from the big orangish download link but I bet it is there, but with a slightly  different name. (Perhaps someone can confirm or suggest another way to  download without clicking the big orangish buton)

The thing is when you click one of those .iso's (or any iso you ever encounter, if I am right) it will do the same  thing it did before unless you right-click and select "save link as"  then go to where it is saved and it should be an .iso.

Hope this helps. If I am wrong about my GUESS as to what is happening... Sorry for the longwinded suggestion.

--timothy4342

---

### Post by mikewhatever on 2011-05-16
> **rahil_evi said:**
> hi all thank you very much 
i have downloaded it using internet download manager.it was downloaded as a zip file .
and so i have extracted it.there comes the problem i am unable to find the iso file .
thanks again 
waiting for help 
rahil

It's not a zip file. Windows sometimes thinks that ISO images are RAR or ZIP files, but that's because you told it to, when installing something like WinRAR.
Just follow the instructions on [http://www.ubuntu.com/download](http://www.ubuntu.com/download), and do not extract anything.

---

### Post by timothy48342 on 2011-05-16
When I click: [http://www.ubuntu.com/download](http://www.ubuntu.com/download)
 I get a page that says,

"Download Ubuntu
You can download Ubuntu online completely free.
Ways to get Ubuntu:"

Ann then there is a link that says, "Try it from a CD or USB stick >"
When I click that, ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)), I get a page that offers 32 or 64 bit versions and has a big button that says, "Start download" (I said it was orange-ish, but I guess its more red-ish.)
Anyway, when I click it I have to choose if I want to open it or save it. Apparently the **O**riginal **P**oster clicks and there is no opportunity to save instead of open. It just opens it as files. Also, the page does not allow the Right-Click menu to come up with the "Save Link As..." option. I think that is what is needed.

When you click the big button you get the file from one of several mirrors, and fortunately when the option window come up it does show the name of the mirror and the exact file name. (for me anyway...)

Following is a link to the file on one of the possible mnirrors that you would get if you went to  [http://www.ubuntu.com/download](http://www.ubuntu.com/download), then clicked  "Try it from a CD or USB stick >" and then selected, "Ubuntu 11.04 - Latest version" and selected "32-bit (recommended)"
[http://gb.releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso](http://gb.releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso)

If your has selected "64-bit" instead, then the link would be:
[http://gb.releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso](http://gb.releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso)

Whatever is messed up with the OP's browser and/or winRAR installation, just RIGHT-CLICK one of those 2 links and select "Save Link As..." and note where you saved it and go to that folder. 
...And there Lo and Behold ought to be an .iso file to be burnt.
Yes? Is it there?

If your still having trouble, please tell us exactly what happens when you do this or that. Meaning exactly what you click and how you click and what happens.

(Also I saw that there exists a .torrent for the .iso. Not the best option as far as security, but maybe as a last resort. If you elect the torrent option you want to trigger the torrent to start from a link directly from the ubuntu site. It is mentined here: [http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt) )

--timothy48342
):P

---

### Post by rahil_evi on 2011-05-31
hey thank you very much it helped !

---

