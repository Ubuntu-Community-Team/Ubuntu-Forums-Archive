---
title: "ubuntu server manual partioned"
date: 2024-01-02
forum: Installation &amp; Upgrades
---

### Post by faustf2 on 2024-01-02
after freash instal of  ubntu  with ssh  i connect by  with my laptop and  i try to copy file   in my home but  tell me  i dont have permission why  ?? i use the same user

---

### Post by yancek on 2024-01-02
There are 3 rows of icons above the text input box and one in the middlerow is insert image.  Mouse over to find it.  Is that what you used?  If you have a partition scheme you can simply post it from a text file or terminal output in QUOTE or CODE tags.

---

### Post by MAFoElffen on 2024-01-02
Please do not insert images inline... Instead use "advanced", go under the text bot to attach the photo as an attachment.

---

### Post by TheFu on 2024-01-02
> **faustf2 said:**
> after freash instal of  ubntu  with ssh  i connect by  with my laptop and  i try to copy file   in my home but  tell me  i dont have permission why  ?? i use the same user

Show the exact command, all options, and be certain to include the usernames on both sides.  It is very easy to try to write to / , which isn't possible, so we need to see the exact command attempted.

ssh doesn't transfer files, BTW.  scp, sftp, rsync are tools that will leverage an ssh connection, but transfer files.  With an account from 2015, it is hard to know what you know.
Did you setup ssh-keys between the systems already?

---

### Post by faustf2 on 2024-01-02
in windows with  win scp work fine but if  use my NB with linux mint mate  not go  bhooo

---

### Post by TheFu on 2024-01-02
> **faustf2 said:**
> in windows with  win scp work fine but if  use my NB with linux mint mate  not go  bhooo

So, no command?

---

### Post by MAFoElffen on 2024-01-03
You lost me.

You went from having a problem installing Ubuntu Server, in the partitioner section trying to do manual partitioning... Which you didn't explain what the problem was, but mentioned you were having troubles on showing us, with some kind of picture you had...

To talking about something with Mint Linux, which that Distribution is not Ubuntu, doesn't have a server edition and is not only "not supported here" in this Ubuntu & it's Flavors (Only) Support Section, but has their own Forum...

To talking about having SCP problems from Windows to something that you never mentioned. scp is not ssh....

Maybe you should start again at the beginning, after collecting and organizing your thoughts.

The points you might want to cover are:
What do you have? What are you trying to do? With what? How are you trying to do that? What are the problems you are having?

---

### Post by TheFu on 2024-01-03
> **MAFoElffen said:**
>  
What do you have? What are you trying to do? With what? How are you trying to do that? What are the problems you are having?

Exactly.  Assume we are 3 yr olds and you have to explain every detail. Don't use abbreviations that aren't specific to Linux, since we are in all different parts of the world. I have no idea what "NB" means.  Is that a distro, software, hardware?  Does it even matter?

For transferring files, we need to know
[LIST=1]
[*]the client OS and version
[*]the server OS and version
[*]the tool being used
[*]the userid on the client side
[*]the userid on the server side
[*]the PWD/CWD on the system running the command
[*]the exact command being run with all options
[*]the exact error message shown.
[*]It would also be good to know what you've tried already, since some commands can impact other, later, commands
[*]
[/LIST]

I think that's it.  Best to do this from a CLI/terminal, since GUI tools don't always work and have 100s of assumptions. With a CLI command, the assumptions are fewer if they aren't completely removed, which is possible, BTW.

---

### Post by ActionParsnip on 2024-01-04
Is Ubuntu Server running on the system? Why are you talking about copying files when the subject of the question is about installing the OS....?
Can you please clarify

---

