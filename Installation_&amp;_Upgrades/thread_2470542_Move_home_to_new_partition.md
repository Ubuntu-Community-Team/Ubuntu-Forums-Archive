---
title: "Move home to new partition"
date: 2022-01-03
forum: Installation &amp; Upgrades
---

### Post by erosman on 2022-01-03
**New to Linux & Ubuntu**

I have installed Ubuntu 21.10 using the default installation option.

It created

```

/boot/efi      512mb
/              931gb

```


I then resized the partitions and created a new partition so now I now have
```

/boot/efi      512mb
/              100gb
               831gb

```

How can I set the new portion as **/home**?

---

### Post by KBar on 2022-01-03
Follow [this](https://help.ubuntu.com/community/Partitioning/Home/Moving) guide and see if it helps. Come back if you have more questions.

---

### Post by erosman on 2022-01-03
> **KBar said:**
> Follow [this]("https://help.ubuntu.com/community/Partitioning/Home/Moving") guide and see if it helps. Come back if you have more questions.
I had seen that page but I didn't find it straight forward for a newbie.
Where did** /media/home **come from?


There is also [How to Create a Separate Home Partition After Installing Ubuntu]("https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/"). Where is devices?

---

### Post by yancek on 2022-01-03
>  Where did** /media/home **come from? 

Read the instructions in the link, you create it.  media is a default directory under / (root of the filesystem) so if you run the command suggested under numbr 4 on thqt site, you create the the temporary mount point and follow the steps after that to copy your files.

---

### Post by erosman on 2022-01-03
Thank you [**[COLOR=#000000]KBar[/COLOR]**]("https://ubuntuforums.org/member.php?u=2162643") & [**[COLOR=#000000]yancek[/COLOR]**]("https://ubuntuforums.org/member.php?u=1928724")
I managed to do it (fingers crossed) using that link.

---

