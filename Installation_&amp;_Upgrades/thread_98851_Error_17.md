---
title: "Error 17"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by M90 on 2005-12-04
Hi well i am fairly new to Linux and have decided to taek another crack at Unbuntu 

so i decided to install it to have a dual boot system with windows xp. So i first off made a 5gig partition with partition magic and then proceeded into Installing Unbuntu.
 unfortantly like last time i tried to install when i got to were i put in my pass word my keyboard does not work.Last time it took 3 different keyboards before one worked and now those 3 same keyboards dont work, So i decided to cancle the installation and when booting i got grub error 17. 

I have tried skipping the password part of the installation. going into windows reapair andhave tryied to fix the boot sector 

I am now in the Unbuntu Live. So any ones able to help me?

---

### Post by bwog on 2005-12-04
Can you give the hardware specifications of you computer? Also, did you format with ext3?

The only things I can say right now that there is no need to use partition magic, and that it can give problems. In the installation procedure there are questions about the keyboard, like typing characters to recognize the keyboard. Did you try that?

---

### Post by M90 on 2005-12-04
Well my comp specs are:
Amd sempron socket a 3000
Ati 9800pro
Msi k7-delta
Ide maxxtor 80 gig HD
Cd-rw cd rom
Hp compaq dvd-rw
1x256 ram
1x512 ram 
and a 450 ocz psu

Xp-pro Sp2
and i did format ext3 journal fileing system

also im not sure what you mean by typing characters to recognize my keyboard what i did do is try every key on the key boards and only the letter and number keys do not work.

---

### Post by bwog on 2005-12-04
During install the installer asks about your keyboard. It can be identified in several ways. One of these ways is typing a few characters.

I would like to add that 5 GB is sufficient, though I would recommend  a larger partition. You can do this later also  if you want to.

---

### Post by M90 on 2005-12-04
uhh well it asks me what country im from and then the my keyboard lay out i think my unbuntu ver might not be herory hedgehog its a realease from mid summer.

---

### Post by bwog on 2005-12-04
Well, I am not sure what you are typing there. However you might try what I mentioned before, or wait for a better answer.

---

### Post by M90 on 2005-12-04
Sorry its early morning here.

Well when im installing Unbuntu it doesent ask to indentify the keyboard it only asks from what country to figerout my keyboard layout is.

---

### Post by bwog on 2005-12-04
Then this option I mentioned will be shown later in the installation proces. I know it is there.

---

### Post by M90 on 2005-12-04
ok well ill go try to install again and see if it comes up

---

### Post by bwog on 2005-12-04
I hope it helps, Good luck.

---

### Post by M90 on 2005-12-04
Nope no go i identified the keyboard but its the same as last time i can type in my user name and name to use to log in but when i get ot the screen to type in my password the letter and number keys dont work

---

### Post by bwog on 2005-12-04
You can type your login name so the keyboard works. When you type the password you get stars so nobody can read it (the password stays secret that way). I suggest you just continue install after typing the password in the two screens that ask for it.

---

### Post by M90 on 2005-12-04
no i dont get stars nothing comes up when i try to type somethign for the password 
i can skip the username and password part of the installation but when i finish the installation and reaboot i get grub error 17

---

### Post by bwog on 2005-12-04
I dont think you can skip this step. But did you actually try typing the password and continu install?  No offence meant ofcourse, but this is very strange because you can  type your login name.

---

### Post by M90 on 2005-12-04
indeed it is strange no offence taken 
ok here is how it goes:
Enter pass word:
 i try to type some thing, nothing comes up. i press enter,
Reaenter password:
i try to type some thing, nothing comes up i press enter,
Password is not secure pleese reaenter pass word. 
i then press Escape a couple times untill i get the a list were i can choose different places in the installation process.
i go to the option after Enter username and pass word.
 It then finishes the Unbuntu installation.
 i reastart the computer 
and take out the Unbuntu Cd it starts to boot
i then get grub error 17 and it hangs there untill i reastart the computer

---

### Post by bwog on 2005-12-04
Do you type the exact same password twice? 

I remember, there is an instruction on screen htat says something about how a secure password should look.

---

### Post by M90 on 2005-12-04
well when i type the password nothign comes up and it is the same also Unbuntu says that no password was typed

---

### Post by bwog on 2005-12-04
We have established that the keyboard works fine. 

But now I am out of ideas, I hope some else can help you.

---

### Post by az on 2005-12-04
[QUOTE=M90]
Password is not secure pleese reaenter pass word. [/QUOTE]

That means that your password must be a certain length.  Are you trying to use a two-character password or something?

Try installing with the password "abc123".  I know that works.  You are not supposed to see anything while typing a password.  That is normal.  And quitting the install by hitting escape will probably leave you with an unbootable system like you have.

To make your Windows install work again, you need to use the recovery option of the windows install cd and fix the mbr.  I think you can also boot a dos floppy and run
fdisk /mbr

but I am not sure since I do not own a computer with windows XP.

---

### Post by M90 on 2005-12-04
ok well it installs fine and accepts the pass word i type in so i think the main problem is that my cd is sratched and theGrub loader is corrupt so my main concer is to get My windows installation working i will try the fix /mbr and see if that helps

---

### Post by M90 on 2005-12-05
well it doesent work and i am getting  this: Nvidia boot angent
: [xe-2.0

Client mac addr:001 09 01 c4 ea
Dxe-e53:no boot filename received

so im not sure what to do.

---

### Post by M90 on 2005-12-05
well it doesent work and i am getting  this: Nvidia boot angent
: [xe-2.0

Client mac addr:001 09 01 c4 ea
Dxe-e53:no boot filename received

so im not sure what to do.

---

### Post by az on 2005-12-05
Is your bios set to try to boot from the network before it tries to boot locally?

Also, did the install finish properly?

---

### Post by M90 on 2005-12-06
Well i have looked around the bios and there doesent seem to be an option to choose were to boot from other than the usaly Ie:hd cd-rom floppy
 The Unbuntu installation seems to install prperly but when ever  i do i get grub error 17 and then i go into windows reapair and reapair the boot loder and then get this nvidia mac address problem

---

### Post by M90 on 2005-12-06
bumb

---

### Post by bwog on 2005-12-06
Your hardware is good for ubuntu, so you should be ables to install.

I have two wild guesses as to why your installation doesnt work.

1) Partition magic messed up your partitions.

2) you have  boot sector protection protection against virusses. This usually gives a different error, but it is not much work to try this:

After install of ubuntu do this [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)
and instead of grub-install /dev/hda you put a floppy in the drive and do this

grub-install /dev/fd0
(yes that is a zero)
try to boot from floppy (check bios boot order).

No guarantees, but good luck :)

---

