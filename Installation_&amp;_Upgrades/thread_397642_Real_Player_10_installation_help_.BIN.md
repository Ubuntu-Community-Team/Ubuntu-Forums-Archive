---
title: "Real Player 10 installation help .BIN?????"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by borisdaniel on 2007-03-30
I've followed the instruction.

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

am a complete newbie to linux so it may seem like a dumb question but i smply did what it ask.

I typed "chmod a+x RealPlayer1Gold.bin" in  terminal window nothing happens

I dont know but i think once i get past the bin i should get a installation screen?

HOW ?? can somebody tell me step by step. exactly what needs to be typed?

thank you.

boris

---

### Post by johnc4510 on 2007-03-30
If you downloaded it to your desktop, try this in your terminal:

cd /home/your_user_name/Desktop

You should see something like this is the terminal:

johnc@Feisty:~$ cd /home/johnc/Desktop
johnc@Feisty:~/Desktop$ 

Now type the chmod a + x command

Then type the install command:

./RealPlayer10GOLD.bin

---

### Post by borisdaniel on 2007-03-31
Here's what am getting??

boris@boris-desktop:~$ cd/home/boris/Desktop/ chmod a + x command
bash: cd/home/boris/Desktop/: No such file or directory
boris@boris-desktop:~$ ./RealPlayer10Gold.bin
bash: ./RealPlayer10Gold.bin: No such file or directory
boris@boris-desktop:~$


i have been using windows for 8 years learning this linux is like just learning how to ride a bike, am falling at every corner. can somebody help me get up LOL

---

### Post by taurus on 2007-03-31
Just replied to your other post.

```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

---

### Post by sylsylveni on 2007-05-24
%Download the .bin file from this link.

[http://www.real.com/linux/](http://www.real.com/linux/)

%type

cd /home/<your user name>/Desktop                % eg <your user name>@ttt

%which should look something like this
% <your user name>@ttt:~$ cd /home/<your user name>/Desktop

%type

chmod 755 RealPlayer10GOLD.bin

% once done with the installation click on applications>sound&video>RealPlayer10
%and you are all set.

%DONE

---

