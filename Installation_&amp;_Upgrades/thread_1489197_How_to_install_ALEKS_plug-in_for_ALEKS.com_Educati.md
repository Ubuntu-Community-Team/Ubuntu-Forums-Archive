---
title: "How to install ALEKS plug-in for ALEKS.com Educational Site"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by lilsim89 on 2010-05-20
This is the method I used to install the ALEKS plug-in for the educational site ALEKS.com. As Ubuntu users should know by now, Linux isn't supported officially. Since the plug-in is pure Java, though, it is by nature cross-platform. 

First, I'd like to point out that I could not install the plug-in successfully using the default Java package on Ubuntu 10.04, so we'll have to remove that using the Synaptic Package Manager:

1.) Open the Synaptic Package Manager and remove the package "OpenJDK".

Now, travel over to [http://www.java.com](http://www.java.com) and download the latest Java Runtime Environment (note, do not download the RPM file, use the BIN). Now install the package using the Terminal (found under Applications >> Accessories)

2.) Make a new Java directory /usr/java by typing in "sudo mkdir /usr/java"

3.) Change to that directory by typing in "cd /usr/java"

4.) Make sure the Java installer is executable by right-clicking it under the File Manager and clicking on "Properties", then "Permissions". Now check "Allow Executing as Program."

5.) In the terminal, execute the program (while still under the /usr/java directory): "sudo /home/<your username>/Downloads/<java installer>.bin".

Now that Java is installed, Ubuntu needs to know how to access it:

6.) Under the terminal, type "PATH=$PATH:<your new Java path>". I reccommend finding the path under the file browser and copying and pasting it. It should be located at "/usr/java/<java version>/bin". Don't forget the "/bin" at the end!

The following will allow Firefox access to the Java plug-in (most browsers obtain their plug-ins from the same directory, so this should work across all browsers):

6.) Change to the mozilla plug-in directory: "cd /usr/lib/mozilla/plugins"

For 32-bit Java: 

7.) sudo ln -s /usr/java/<java version>/plugin/i386/ns7/libjavaplugin_oji.so 

For 64-bit Java:

7.) sudo ln -s /usr/java/<java version>/lib/amd64/libnpjp2.so

Now that Java is installed and configured, let's go to ALEKS.com and get the plug-in to install. 

8.) Download the JAR file from [http://www.aleks.com/downloads](http://www.aleks.com/downloads) and save it where you can find it.

9.) In the terminal, use "sudo nautilus" to open the file browser with administrator permissions. Now find the ALEKS plug-in you downloaded and right-click to copy it. Now go to the Java plug-in directory: "/usr/java/<java version>/lib/ext" and paste it.

10.) Restart your browser and the ALEKS website should work without any problems.

I hope this guide helped you, but please don't hesitate to post any comments, questions, or corrections.

---

### Post by werecatomega on 2010-06-04
doesn't seem to work for me
when i try on firefox it seems to work but then possible the funniest thing ever happens



Sorry, the page your requested was not found


Please check the URL "/alekscgi/x/Isl.exe/1cyAUkjTwklGkUe8Hg8y3gRvSWxdBzfCaw4TJ9MLlxdtFOEcE8m8OYYPkm-aoo6CK2n8TfsQzHQV-r8Ph1JKRyNsp8TrZAJKE_fC5Cn8mvgkkpKoa_1QYytltVYKQbt_B6qQ0OkW_IR7Z5vy6TtPgKpHICEtTDRtue_FIJuhKIycfQt5f14IOf-N1HwiJmIneCin4Cpdxb5H4zO4EgtRYstbuzmn5nsbwwwBcn9wZsDYZeDZI5HHSrJ1XLVKt2UGhLhpv7NLU3YoPecCeyIeiOUhoVgKKzFgD0KCImPyPTYPsPCODYwiO_v3ajrjHErBcIKnQZRaXEvRkbTdf_Mx6WEzJtAm1FlMynydGIH5P1GyuqT-8lhXa5256_q5t8WTWEjoreCM9rpASUfZvKxWjKdP-ElG9o3g721RXuqkojdVpt19JaNRW0jLLcUOhdJzOkMSRjU-VaRorCUh4Mmq1-sBlnznLG7lFgu0STsP-3tv12fqLV1YWElO88wlNVt6f1OZuhyg4eaWuF".
Other things to try:

    * Search [www.aleks.com:](www.aleks.com:)

 

If you need help regarding this problem, please contact us at [http://support.aleks.com/webmaster](http://support.aleks.com/webmaster)

 

[Back to Home Page]

 

lol, 404 error

---

### Post by hectoralex on 2010-09-06
WORKED WONDERS FOR ME! ):P Thank You!

---

### Post by jackechanprime on 2010-09-11
K, now i've got a new problem for you...

Aleks fully installed and "functional."
Program is loading and initializing smoothly, program comes online and is (apparently) completely operational... *HOWEVER*...

The actual problem interfaces (as it's a math homework program, it has interfaces where you input your final answer as well as "buttons," which are some form of script link, for getting explanations as well as other basic GUI functions within the program (back, next, done, etc.). *THESE SCRIPTS ARE NOT RUNNING*. The result is that when i attempt to actually perform the point of the program and solve a homework problem, *I CANNOT ACTUALLY ANSWER IT*. not only that, but even if i could answer it, without the "done" button rendering, i cannot actually submit my answer!

Ask anything you need to know, and i'll tell you.

ubuntu 10.04, firefox 3.--something (latest), jre6 (reinstalled literally yesterday, so should be the latest version, most importantly, jre IS working.)

Any help GREATLY appreciated. like everyone else who seems to be having this problem, if i cant get ALEKS running right, i automatically fail this math course.

---

### Post by hectoralex on 2010-09-13
I have the same problem, but I have figured out that if Iclick anywhere on the page and back onto the answer box it will work.  But just sometimes i have click on another window or tab by bringing it to the front and then returning to the window or tab with aleks running on it... it will finally allow the input in the answer prompt.

Notice that either tab or window, or even selecting other program, a file explorer window and then returning to the aleks tab will allow input.

To Summarize... Just minimize the browser window and maximizing it will allow for input of answer once again...

):P

> **jackechanprime said:**
> K, now i've got a new problem for you...

Aleks fully installed and "functional."
Program is loading and initializing smoothly, program comes online and is (apparently) completely operational... *HOWEVER*...

The actual problem interfaces (as it's a math homework program, it has interfaces where you input your final answer as well as "buttons," which are some form of script link, for getting explanations as well as other basic GUI functions within the program (back, next, done, etc.). *THESE SCRIPTS ARE NOT RUNNING*. The result is that when i attempt to actually perform the point of the program and solve a homework problem, *I CANNOT ACTUALLY ANSWER IT*. not only that, but even if i could answer it, without the "done" button rendering, i cannot actually submit my answer!

Ask anything you need to know, and i'll tell you.

ubuntu 10.04, firefox 3.--something (latest), jre6 (reinstalled literally yesterday, so should be the latest version, most importantly, jre IS working.)

Any help GREATLY appreciated. like everyone else who seems to be having this problem, if i cant get ALEKS running right, i automatically fail this math course.

---

### Post by jackechanprime on 2010-09-13
nonono, it was worse than that. The entire thing wasn't rendering at all. There was no interface to interface with, or buttons to click on, or even a gray placeholder box. It was like the scripts were locked in "loading" mode, but never actually loaded.

O_o however, the problem mysteriously resolved itself last night, and for some reason now they ARE rendering. I didn't even do a system update, and the problem just decided to fix itself. I'm totally stumped.

Anyway, NOW i'm having the little glitch that you described happen on occasion, which honestly doesn't bug me at all. Thanks for the tips anyway!

O_o back to pondering the mysteries of Ubuntu... (and math homework)
~Q

---

