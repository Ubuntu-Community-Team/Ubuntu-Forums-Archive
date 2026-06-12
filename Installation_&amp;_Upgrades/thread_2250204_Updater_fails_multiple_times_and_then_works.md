---
title: "Updater fails multiple times and then works"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by JohnBlood on 2014-10-27
When I try to update Xubuntu on an office PC, it fails at least twice before it works. It says that it failed to download repository info. It should work one the first try because we have really fast internet. What's the problem?


[[IMG]http://www.zimagez.com/miniature/screenshot-10272014-103456am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-10272014-103456am.php")

---

### Post by ian-weisser on 2014-10-27
Try it from a Terminal so you can capture the error messages that will tell you the problem.
```
sudo apt-get update
sudo apt-get upgrade
```

If you're not sure what the error message means, we can help you.
copy-and-paste the entire terminal output here. Use [code] tags to contain the output.

---

### Post by JohnBlood on 2014-10-27
> **ian-weisser said:**
> Try it from a Terminal so you can capture the error messages that will tell you the problem.
```
sudo apt-get update
sudo apt-get upgrade
```

If you're not sure what the error message means, we can help you.
copy-and-paste the entire terminal output here. Use [code] tags to contain the output.

The person who uses the machine does not have admin privileges. How do I use sudo apt-get in the terminal from her account?

---

### Post by grahammechanical on 2014-10-27
What version of Xubuntu are you running on that machine? I ask because I am getting that same message. I am not surprised to get that message because I am running the next development version of Ubuntu (Vivid Vervet). I click OK and then Software Updater appears as usual and things go as they should. That message could be appearing because there are repositories listed as software sources that Software Updater cannot connect to. Running those two commands will show if that is the case.

When we install Ubuntu or Xubuntu for that matter we have to provide a password that will be used to authenticate certain actions. That password can be kept secret from the normal user of that machine. But someone should know the password.

It is also possible to set a user as a standard user whose password would not authenticate certain actions. But there first has to be an account for an administrator.

Regards.

---

### Post by JohnBlood on 2014-10-27
> **grahammechanical said:**
> What version of Xubuntu are you running on that machine? 
 
I just updated it to 14.10 last Friday.

---

