---
title: "unable to update"
date: 2015-09-16
forum: Installation &amp; Upgrades
---

### Post by Jim_Dodds on 2015-09-16
I tried installing monolight and now somehow I messed up update manager. when I do sudo apt-get update it says the list of sources could not be read. executing is not known on line 1 in source list /etc/apt/sources.lists.d/mono-xamarin.list

How do I fix this issue????

---

### Post by Bucky Ball on 2015-09-16
You kill the monolight PPA you installed attempting to install monolight.

Open 'Software and Updates'> Other Software tab. Look for anything with 'monolight' in it or related to 'mono' and untick or remove it.

---

### Post by Jim_Dodds on 2015-09-16
There is nothing in there with monolight??

---

### Post by deadflowr on 2015-09-16
Run the following command  and Post the output
```
cat /etc/apt/sources.lists.d/mono-xamarin.list
```
so we can see what the line actually says.

---

### Post by Bucky Ball on 2015-09-16
As deadflowr says. And also, how did you install it? Or try?

---

### Post by Jim_Dodds on 2015-09-16
There is nothing in there with monolight??

I followed the instructions on the monolight page I got as far as installing the signature? and failed at the rest  
```
[COLOR=#0086B3][FONT=Consolas]sudo[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] apt-key adv --keyserver hkp://keyserver.ubuntu.com:[/FONT][/COLOR][COLOR=#009999][FONT=Consolas]80[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] --recv-keys [/FONT][/COLOR][COLOR=#009999][FONT=Consolas]3[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]FA7E0328081BFF6A14DA29AA6A19B38D3D831EF[/FONT][/COLOR][COLOR=#0086B3][FONT=Consolas]echo[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] [/FONT][/COLOR][COLOR=#DD1144][FONT=Consolas]"deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy main"[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] | [/FONT][/COLOR][COLOR=#0086B3][FONT=Consolas]sudo[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] tee /etc/apt/sources.list.d/mono-xamarin.list[/FONT][/COLOR][COLOR=#0086B3]
``````
sudo apt-get update
```

I run the code and it says no such file or directory

---

### Post by deadflowr on 2015-09-16
Odd.
Since that's the file you posted as having an error.

is there anything listed, maybe similar to the file name you posted, if you run
```
 ls /etc/apt/sources.list.d/
```
?

**Edit:** Oh, you added an 's' to list.
Try rerunning the cat command but remove the s from lists, so it only says list.

---

### Post by Jim_Dodds on 2015-09-16
```
executing is not known on line 1 in source list 
/etc/apt/sources.list.d/mono-xamarin.list
the list of sources could not be read  
google-chrome.list 
google-chrome.list.save
mono-xamarin.list
mono-xamarin.list.save
pipelight-stable-trusty.list
pipelight-stable-trusty.list.save
precise.list.save
web8team-java-trusty.list
web8team-java-trusty.list.save
```

I unchecked monolight and nothing

---

### Post by matt_symes on 2015-09-16
Hi

From the terminal type this command

```
sudo rm /etc/apt/sources.list.d/"*source*"
```

Check then double check the command is exactly the same as mine before hitting enter.

Then type ```
sudo apt-get update
```

Post back any errors after.

Edit: please post the full text from the terminal using code tags.

Kind regards

---

### Post by Jim_Dodds on 2015-09-16
cannot remove '/etc/apt/sources.lists.d*source*': No is what happens after I run the command

---

### Post by matt_symes on 2015-09-16
Hi

That command is not the same command I typed for you.

You may find it easier to copy and paste the command I typed and paste it into the terminal window so you don't make any typos.

Kind regards

---

### Post by Jim_Dodds on 2015-09-16
I copied letter per letter same response? How do I copy and paste to Xterm?

---

### Post by howefield on 2015-09-16
> **Jim_Dodds said:**
> I copied letter per letter same response? How do I copy and paste to Xterm?

Copy from here (highlight then Ctrl + c) then use the Shift + Insert keys to paste into Xterm.

---

### Post by Jim_Dodds on 2015-09-16
I copied and pasted like you said and response.

---

### Post by Jim_Dodds on 2015-09-16
No such file or directory

---

### Post by matt_symes on 2015-09-16
Hi

There is also a typo in my command. Use this one instead

```
sudo rm /etc/apt/sources.list.d/*source*
```

Somehow *sources* got sorrunded by quotes. Not what I wanted.

I'm blaming this phone. Either that or I'm going senile young.

Kind regards

---

### Post by Jim_Dodds on 2015-09-16
[COLOR=#000000][FONT=Ubuntu Mono]sudo rm /etc/apt/sources.list.d/*source*   same response no such file or directory?[/FONT][/COLOR]

---

### Post by matt_symes on 2015-09-16
Hi

We're not having much luck at the moment :/

Let's have a look at all the files.

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Please please please copy the output from the terminal. Show me what it is and don't tell me what it is. I need to see the terminal output.

Please use code tags like this

[noparse]```
text from terminal
```[/noparse]

To get output like this

```
text from terminal
```

Kind regards

---

### Post by Jim_Dodds on 2015-09-16
how do I copy from the teminal Xterm?

---

### Post by Jim_Dodds on 2015-09-16
It basically shows me everything that is in othersoftware

---

### Post by Jim_Dodds on 2015-09-16
what is the easiest way for me to reinstall ubuntu and put wily on here. I'm runnning Chrobuntu

---

### Post by matt_symes on 2015-09-16
Hi

If you are not prepared to follow the instructions I need to be able to help you then I cannot help you.

So far you have posted an error for files that do not seem to be on your system.

I cannot see what you are seeing and you do not seem prepared to help me see what you are seeing.

Take a look at some of the other threads on the forum and look at the posting styles and the information exchange. That'll help you know how and what to post to get the best help.

I'm afk for an hour now.

Kind regards

---

### Post by Bucky Ball on 2015-09-17
DO NOT install Wily. It is not even released yet and you are having a heap of trouble getting anything fixed on a stable release. :)

To copy from the terminal, control+shift+c.

We can't help much until you can start getting the whole output code up here for us to look at.

---

### Post by matt_symes on 2015-09-17
Hi

If you are using xterm then you need a slightly different way to copy text from the terminal.

Highlight the text to copy in the terminal. This will copy it into the primary buffer automatically.
To paste it into your post, position the cursor into the text area of the post at the point where you want the text to appear and click both the left and right mouse buttons at the same time. This will paste the text.

For most other terminals, you'll want to use BuckyBall's solid steps in the previous post. 

Xterm is an oddball terminal. I recommend not using it unless you have to.

Kind regards

---

### Post by Jim_Dodds on 2015-09-17
[COLOR=#000000]To copy from the terminal, control+shift+c.   [/COLOR][COLOR=#000000]Highlight the text to copy in the terminal. This will copy it into the primary buffer automatically.[/COLOR]
[COLOR=#000000]To paste it into your post, position the cursor into the text area of the post at the point where you want the text to appear and click both the left and right mouse buttons at the same time. This will paste the text. None of these ways for me to copy and paste from the terminal are working I can copy and paste to the terminal but that is no help. I can't install any other terminal since I can't update right?? I tried atleast.[/COLOR]

---

### Post by Sweet_Baby_Jamie on 2015-09-17
[I][COLOR=#000000]I can't install any other terminal since I can't update right??

[/COLOR][/I][COLOR=#000000]Correct.  You're stuck with what you have until you have.  But I really suggest that you simply download a current supported version of Ubuntu!  If you're not comfortable with making your own bootable DVD, then I suggest ordering a ready-made DVD of the latest Long Term Support release*[COLOR=#000000] [/COLOR]*(from Canonical or OSDisk.com).[/COLOR][I][COLOR=#000000]


[/COLOR][/I]

---

### Post by matt_symes on 2015-09-17
Hi

> **Jim_Dodds said:**
> [COLOR=#000000]To copy from the terminal, control+shift+c.   [/COLOR][COLOR=#000000]Highlight the text to copy in the terminal. This will copy it into the primary buffer automatically.[/COLOR]
[COLOR=#000000]To paste it into your post, position the cursor into the text area of the post at the point where you want the text to appear and click both the left and right mouse buttons at the same time. This will paste the text. None of these ways for me to copy and paste from the terminal are working I can copy and paste to the terminal but that is no help. I can't install any other terminal since I can't update right?? I tried atleast.[/COLOR]

I use xterm regularly so i can't understand what is going wrong. Here's my copy and paste from xterm.

```
matthew-laptop:/home/matthew % echo $TERM
xterm
matthew-laptop:/home/matthew %
```

It's hard to help you if we cannot get the information. I don't think its' your fault; there could be many reasons. I'm sorry that, so far, this visit to the forums has not been useful to you.

We could redirect the output from xterm to a file and attach that to posts but to be honest i would just reinstall.

There are many people who can help you to that and i'm sure they jump in to help.

Kind regards

---

### Post by Jim_Dodds on 2015-09-17
I just reinstalled. I want to thank everyone for their help.

---

### Post by Bucky Ball on 2015-09-18
If all is good, please see the first link in my signature to mark as solved. Don't hesitate to post a new thread for any new issues. Good luck and enjoy the ride. :)

---

### Post by Sweet_Baby_Jamie on 2015-09-18
If you installed a *current* version of Ubuntu your problem is SOLVED!  If you *re*-installed the old unsupported one, you're starting from scratch again with the same old problem!  What did you install?  (Your post indicates that you "*re*-installed")

---

### Post by Jim_Dodds on 2015-09-18
Trusty

---

