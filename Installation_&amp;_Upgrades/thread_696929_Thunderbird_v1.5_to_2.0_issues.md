---
title: "Thunderbird v1.5 to 2.0 issues"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by LT72884 on 2008-02-14
Ok so i went into add/remove programs and added thunderbird. It downloaded v1.5. I set up my mail account and that works but themes dont work for it becasue it needs to be v2.0. So i go to tools and try to do check for updates but its all grayed out. Mozila.org has the tar.gz for v2.0. I grab that along with the install instructions. The instructions are as follows:
---------------
   1.  Make a temporary backup of your profile(s).
   2. Open a shell (terminal) and decide where you want to install the new version. Remove the old Thunderbird directory if you want to install over an older version; this does not remove your profile data.
   3. Go to the directory you want to install Thunderbird, using the command: cd /path/to
   4. Extract the downloaded Thunderbird "tar.gz" file: tar -xzvf /path/to/thunderbird-<version>-i686-linux-gtk2+xft.tar.gz
   5. When finished, launch Thunderbird with the command: /path/to/thunderbird/thunderbird
   6. Thunderbird should pick up your profile information automatically and be ready to use. 

Hint to newbies: To avoid (mis)typing long file names, like Thunderbird's *.tar.gz file, merely type the first two or three letters, then press your tab key. The terminal program will fill the rest out for you. 

----------------

Ok so this is what i did exactly. I skipped step one becasue i dont care abut my profile. Step 2 i created a folder under this path. /home/Lt72884/thunderbird.

Step 3 i did a cd to /home/Lt72884/thunderbird and performed the following command.

tar -zxf /home/Lt72884/Desktop/thunderbird-2.0.tar.gz

Step 4 i did a ls and it showed the thunderbird folder. now the path looks like so 
/home/Lt72884/thunderbird/thunderbird

i then typed this at the command prompt

thunderbird. 

it replied with

bash thunderbird command not found.

I followed the directions correctly. step 1 said i could choose were i wanted to install it. So how do i update it and why cant i update it through tools>check for updates???

thanx guys

---

### Post by LT72884 on 2008-02-14
ok something strange. i went into the actual folder thunderbird using the GUI and i saw a file named thundebird. so i double clicked it and ran it in terminal. now v2.0 opens but when i close it and go to applications>internet>thunderbird email

it opens v1.5

---

### Post by LT72884 on 2008-02-14
Ok i think i figured it out. found where the thunderbird was installed and so i deleted everything in the directory. then i copied the tar file over to the directory and extracted it there. then  i right clicked on the applications bar and went to edit menus. i clicked on internet and then thunderbird. i edited the launch properties. Where it says launch command i browsed for the new exe in the extracted thunderbird folder.

so far it works. I hope it continues to work.

hmmm i dont think this is going to work. It wont play any sounds and it wont automatically download and check for new messages. I have it set up right. I have been using thunderbird with windows for over a year now. I wonder why it wont grab my messages automatically. it will only grab them and download them if i hit get new messages.

---

### Post by LT72884 on 2008-02-14
no go with that idea.

---

### Post by LT72884 on 2008-02-15
i cant get it to work. So far all i have done was extract the upgrade folder to this path:

/home/Lt72884/.thunderbird

once i did that the path looks like this:

/home/Lt72884/.thunderbird/thunderbird

Then i edit the menu launch command in applications>internet>thunderbird to point to the executable in the /home/Lt72884/.thunderbird/thunderbird folder.

It works to a point but with some issues. The first issue is that it wont check for mail automatically. I have a comcast.net address and i have thunderbird configured to download my messages automatically every 1 minute. For some reason it doesnt want to grab them. The sound doesnt work in it either for when i do recieve new messages. 

I would like to get this fixed and running correctly. 

Thanks guys

---

