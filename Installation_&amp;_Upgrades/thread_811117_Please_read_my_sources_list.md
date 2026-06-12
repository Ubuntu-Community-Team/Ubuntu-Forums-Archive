---
title: "Please read my sources list"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by randywilharm on 2008-05-28
I upgraded to Hardy last week with almost
successful results.

I wonder--if I should reinstall Hardy or
maybe there's a repair option on the disk
i don't know about.

I tried to install Cineleera and now it's
a broken package I can't remove!!

I actually could'nt copy and paste the
terminal readout so I included it
and another message in PNG format

It says I have duplicate entries but I don't
know which to remove..
Any advice is appreciated....

---

### Post by iaculallad on 2008-05-28
> **randywilharm said:**
> I upgraded to Hardy last week with almost
successful results.

I wonder--if I should reinstall Hardy or
maybe there's a repair option on the disk
i don't know about.

I tried to install Cineleera and now it's
a broken package I can't remove!!

I actually could'nt copy and paste the
terminal readout so I included it
and another message in PNG format

It says I have duplicate entries but I don't
know which to remove..
Any advice is appreciated....

You could try doing this:

On your terminal, issue this commands:

Code (Add the repo):

```
sudo wget http://repository.akirad.net/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
```

Code (Add the Auth key):

```
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

Code (Now you install it):

```
sudo apt-get install cinelerra-generic
```

---

### Post by randywilharm on 2008-05-28
No, it does'nt work

I should have mentioned that I an not

concerned with cineleera at this point.

I cant run the package manager

I get only partial updates

should I reinstall Hardy????

---

### Post by iaculallad on 2008-05-28
On the terminal:

Code:
Backup sources.list first

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

Code:
Open sources.list and delete all its content then save it (your saving a blank file here).

```
sudo gedit /etc/apt/sources.list
```

Navigate System->Administration->Software Sources, and check Main, Universe, Restricted, Multiverse. Select "Main Server" for "Download From" and be sure to uncheck (if it's checked) the "Installable from CDROM-DVD" box. Click on "Close" button to reload. Redo your update. Hope this could work.

---

### Post by randywilharm on 2008-05-28
MOST of that last solution

worked as I can now run the package manager

but I went to synaptic and it tells me

i've got 2 broken packages (cineleera-related)
I tried the "fix packages" option but they just stay there

It refers to "error 1"-- I think I enclosed a PNG above
regarding this---

I appreciate what your doing and I don't like to
keep bothering you but I can't walk out on half a job

I will abort the Cineleera installation if need be

I thank you for your trouble with this..

---

### Post by randywilharm on 2008-05-28
strike that---

my package manager still has the red arrow

---

### Post by iaculallad on 2008-05-28
Like what the error message states, run the command on your terminal

Code:

```
sudo apt-get -f install 
```

to correct file dependency.

But before doing that, execute the commands on my very first post first to place Cinerella's repo on sources.list file.

---

### Post by randywilharm on 2008-05-28
o.k., thanks, i'll try it--have a good night

---

### Post by randywilharm on 2008-05-28
I did everything above and in the proper order

and I still have the two cineleera packages (broken)

that just WON'T go away. Tried "fixing them" reinstalling them

and i've still got the red arrow on my package manager

I'm really starting to think

I need to reinstall Hardy or just go back to Gutsy

where things worked fine, but i'll try to stick with it.


I think the PNG image with the error message I enclosed

may provide a clue but it's a little hard to understand,

Thanks again.....

---

### Post by iaculallad on 2008-05-28
Can you post the error that shows when you type the command:

```
sudo apt-get install cinelerra-generic
```

on your terminal.

---

### Post by randywilharm on 2008-05-28
this is it-------

---

### Post by iaculallad on 2008-05-28
> **randywilharm said:**
> this is it-------

On that same terminal, issue the command **sudo apt-get -f install** to resolve dependencies.

Code:

```
sudo apt-get -f install
```

Then retry installing Cinerella.

---

### Post by randywilharm on 2008-05-28
here it is--

The repetitive entry between procedures

was made by me deliberately so it

would be easier to see.

---

### Post by utUtu on 2008-05-28
> **randywilharm said:**
> this is it-------

Why don't you install libmpeg3hv-generic first?

---

### Post by randywilharm on 2008-05-28
sounds like a good idea--

i want to see what this other chap

says before I do though, Thanks

---

### Post by utUtu on 2008-05-28
> **randywilharm said:**
> here it is--

The repetitive entry between procedures

was made by me deliberately so it

would be easier to see.

Looks like there is  a conflict between mpeg3-utils package and the libmpeg3hv-generic.  Try removing the mpeg3-utils, and see if it works.  There could be breakage.

---

### Post by iaculallad on 2008-05-28
Just finished installing Cinerella on my system with no errors incurred. You could try installing libmpeg3hv-generic first then do your reinstall.

---

### Post by randywilharm on 2008-05-28
Thanks to both of you---

I'm going to give it a try..

---

### Post by utUtu on 2008-05-28
> **randywilharm said:**
> sounds like a good idea--

i want to see what this other chap

says before I do though, Thanks

Look at my 2nd post.  I saw it being installed but there's an error based on your 2nd attachment.  The problem is there's a conflict with mpeg3-utils.  Like I said try removing it.  There could be breakage.

---

### Post by iaculallad on 2008-05-29
Or if this could be of help with you, try visiting the [Akirad Project]("http://www.akiradproject.net/repository"), the maintainer of Cinelerra.

---

### Post by randywilharm on 2008-05-29
IT WORKED!!!! SUCCESS!!!!

The solution was somwhere between what both of

you said....I now have CINELEERA on my computer

for the first time!!!

You'll understand why I need it if you check out
my youtube site:

[http://youtube.com/randywilharm](http://youtube.com/randywilharm)

It's primarily pre-1970 scifi cinema and
i'm trying to add quality graphics to it.


Thanks again, guys....
I'll stick with Hardy now.
Ubuntu is the best thing i've discovered.
Your immune to viruses and spyware with it (immune enough)
and that dissolves a lot of stress...

---

### Post by iaculallad on 2008-05-29
Glad to hear that your Cinelerra worked. Goodluck with it. Go Ubuntu

---

