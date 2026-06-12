---
title: "Problems with synaptic and medibuntu"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by Alephlex on 2008-03-06
Hi,

I ran into problems trying to install Skype using the Medibuntu Repository.

I followed the instructions here:
[http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/)

I started feeling that something went wrong midway through using the terminal window to get the medibuntu package. I was prompted for my password which I entered. I was then returned immediately to the command promp.After that I tried to get the GPG key for the medibuntu package. That returned the following message: no valid openPGP data   
 found.

When i next tried to open synaptic, I got the following message:
E: type '--18:19:50--' is not known on line 1 in source list/etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache-> open () failed, please report

I am running Gutsy Gibbon Ubunto 7.10 on a Fujitsu Lifebook S7110.
Can anyone please help?

Please excuse me if the post is amateurish. I am a total newbie. And could you please help by giving me very simple instructions because I know next to nothing about where to find basic stuff in Linux. I will be trying to get an education on this soon.

Also, my keyboard seems to be responding in a funny way. I might be in the middle of typing when all of a sudden, my cursor gets shifted to a different line on the page (about 3 lines up). Is this a problem with the keyboard driver? The characters are all recognised ok and the keyboard layout is correct.

Thanks for your help in advance.

---

### Post by forestpixie on 2008-03-06
At a guess I'd say it went horribly wrong :) - easy fix though

open the file for editing using gksudo gedit 
```

gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

it will likely be full of rubbish - delete it all and save the file

then redo the medibuntu thing - ina terminal 

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

should sort it for you

---

### Post by Alephlex on 2008-03-06
I tried your suggestions.

I did get a file with some unusual commands in it when I opened it through gedit. So I deleted the material and saved the file.

This cleared up the synaptic manager.

Then I tried to get the distribution through the terminal window again  -- incidentally, that's how I tried to get it the last time too.

I got the same message in synaptic except that the numerals in the top line had changed from --18:19:50--  to  -- 20:45:09 -- 

Is there anything else I can do?

Thanks

---

### Post by PmDematagoda on 2008-03-06
Remove the file with:-
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
Update the sources list:-
```
sudo apt-get update
```
And then try adding the Medibuntu repositories again.

---

### Post by Alephlex on 2008-03-06
I'd like to thank you all for putting in your suggestions.

After running the rm code to remove the references to medibuntu, my synaptic manager started performing normally again.

Repeated attempts with the medibuntu repositories produced the same result as the original post

So I eventually solved the problem by by-passing the medibuntu repositories and doing a direct download from skype.com itself. The programme is now up and running and synaptic works fine too.

Thank you all for taking the time to help.

---

### Post by zvacet on 2008-03-07
I belive you will use medibuntu repo in future so add  it to your source list

```
gksudo gedit /etc/apt/sources.list
```

add line

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
[B]
If you use Gutsy replace feisty with gutsy in that line[/B]

save and close

In terminal

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

---

