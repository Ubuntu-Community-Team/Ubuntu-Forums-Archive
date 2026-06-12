---
title: "Python will not run, Root Terminal is non-existant"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by machdohvah on 2013-04-26
Hi... I just installed the new release of Ubuntu 13.04 and found that my python scripts will not run even after giver it permission. I have also noticed that Root Terminal and access to the "Comupter" folder where each device is listed such as /Files. Why does the Adminstrator not have access to root? Do I have to give myself access in the user definition app?

I had to re-install 12.10 to save my system. 13.04 currently does not allow the Administrator to have access to the root terminal. Consequently, many other operations that require this access is also lost. For example, when I started to view a movie (AVI) file, it tried to download some files. It failed to do so and the movie player box just froze. When I tried to download extra card files for Aisleriot Solitaire, it failed to find the catalog. Please, understand that I intend to use 12.10 until these bugs are resolved.

As far as Python is concerned, I found that only an in terminal applications may be run. In 12.10, it is simple thing to allow the PY file to run as an application and then it would work. This is lost in the current 13.04. I finally found the "Computer" folder and therefore access to the root was available there. I feel like I am a locked user in my own Administrator.

---

### Post by ibjsb4 on 2013-04-27
Could it be ..

[http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-raring-13-04/284717#284717](http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-raring-13-04/284717#284717)

---

### Post by pietrvanhelsing on 2013-04-27
Okay, here's a workaround; you can run the python script by direct invocation in a terminal. What you need to do is wrap the python script in a shell script and try that. I'm going to try it now. I'll let you know if that works.

---

### Post by pietrvanhelsing on 2013-04-27
This:
[http://askubuntu.com/questions/286208/after-charging-the-permissions-why-cant-you-execute-a-run-shell-lscript-from]("http://askubuntu.com/questions/286208/after-charging-the-permissions-why-cant-you-execute-a-run-shell-lscript-from")
fixes shell scripts and python scripts.

---

### Post by machdohvah on 2013-05-01
You are all missing the point. One of my clients who allowed 13.04 to be installed, found that she suddenly could not even get to her Yahoo Mail. The this freezes on her. I have noticed many places in 13.04 where it freezes. 13.04 is simply not ready to be released. It should be pulled back from release and tested further.

---

### Post by MAFoElffen on 2013-05-02
If both bash and python are boinked, something is very seriously wrong. 

I'm still writing python app's and bash scripts... On 13.04... python 2.7.4 and 3.x... and I have no problems with 13.04 "freezing" anywhere.

First, at a terminal prompt:
```

python -V && echo "$BASH_VERSION"

```
Here is my output to that:
```

mafoelffen@maferr-ubuntu-1:~/Documents$ python -V && echo "$BASH_VERSION"
Python 2.7.4
4.2.45(1)-release

```

>> "my client..."
So is it "your" scripts that are not working or all scripts?

If "your's", check your script by starting it via:
```

python -3 script_name.py

```
Than will warn about Python 3.x incompatibilities that 2to3 cannot trivially fix... And take note that by v14.04 all python scripts need to be v3.x compliant.
[https://wiki.ubuntu.com/Python/3](https://wiki.ubuntu.com/Python/3)

---

### Post by machdohvah on 2013-05-03
Uh, I think it is obvious that after a fresh installation of 13.04 and that another user confirmed the problem means that it is truly serious. Again, many scripts do not work anymore such as Yahoo Mail. Please, get it together people. This 13.04 has not been tested enough to be published. Please review this package and take it off the market. Fix it and re-publish it as a revision of the older one. Pretty please. This is quite embarrasing for Ubuntu in general and needs to be looked at. So far, all I am getting is that you people believe that MY system is somehow unique. How can that be in a fresh install of 13.04. I have great success with 12.10 and I hope that it will be supported long into the future. I am already having to install "gnome-session-fallback" each time to get the "Vista like" desktop to appear. After that, there many changes that I have to make to even get it to be useful. I would be glad to convey the entire "Installation List" that I have to use in each installation. :)

---

### Post by oldos2er on 2013-05-03
If you want your issues taken seriously, file a bug on launchpad.net, otherwise the developers have no way of knowing about it.

---

### Post by MAFoElffen on 2013-05-04
It is apparent the the op is not having "the problem"... He is reporting problems secondhand. If the person or people having the problem were to post here... or on launchpad, those could be dealt with. This Op has not answered any of my questions.

On a bug search- No one else has reported Ubuntu Desktop provided Python scripts, programs or problems with the python install scripts in 13.04. I know there is a current project to convert all the system's python scripts to 3.x by 14.04LTS as a goal for python 2.x to "go away." But I don't think that is a part of what he is talking about.

Here's my take on this. The OP said: "His customers" "Yahoo mail script", other tidbits... Ubuntu does not have a python script for yahoo mail in it's desktop suite. Earlier he said both python and bash was not working. If this was so, the system would be static and not be able to do anything. None of the desktop app's would run. The system is very much dependent on both bash and python.

As a +1 dev tester... I understand the release structure. 12.04 is LTS. All others besides LTS are rolling snapshots. As a python programmer, I am actively pushing python to it's limits in 13.04. I can confirm that I have not had any problems with python 2.7.4 (default for 13.04) or 3.0, 3.1, 3.2 or 3.3. I do know that python 2.7.4 is a ramp-up for 3.x and some things are more stringent and "deprecicated"... meaning somethings that worked earlier and are now changed, that if they are at least coded to 2.7.4 are not going to work. As far as I know, everything I've seen "in" 13.04 is there.  Pyhton is upstream code above Ubuntu. Ubuntu is planning for the changes in Python... Just as it had to from Gnome 2.x to 3.x.

Now on 3rd party python scripts (such as one for "yahoo mail"), that's anyone's guess. There was a python recipe for that that included customized libraries from sourceforge... I think I remember that was coded to python 2.4 conventions and Yahoo has changed "how" their forms work since then. If he's using "expect" to do it in a bash script (he mentioned bash scripts not working also), any changes in their forms will effect that. Communications is the understanding between two sides... Not just on slamming Ubuntu blindly without making any attempt to resolve anything. Now if his customer's are using his yahoo mail script... and it is now having problems... if he starts the script with a "-3" option (like I posted above), it will tell him what he needs to change to get it compliant with python 3.x. But I really can't tell for sure "what" the specific problem is. That has not been identified. Confusing, yet a curiosity.

I'm not having any problems with my own bash or python scripts. But right now I have my python IDE set to python 2.7.4 conventions as a minimum. I'm thinking that in June, I reset my minimum conventions to python 3.0, looking towards 14.04.

I'm just here to help people. If you want help, I'll do my best to help you, your "customers", their friend's cat... etc. But if I ask for info to help me in resolving a user's problem and I get blown off, it's hard to take that seriously and keep focus. I'm sure you can understand that.

If there is a problem, have the person having the problem join in here so we can objectively resolve it. That is the goal right? To resolve problems? If it can't be resolved here, then it surely is a bug to be reported so it can be resolved.

---

### Post by machdohvah on 2013-05-10
I am not an Op, sorry. This has been submitted to Launchpad. It is actually a plea for the release of 13.04 to un-released for practically everything freezes up on the thing.

---

### Post by coffeecat on 2013-05-10
> **machdohvah said:**
> I am not an Op, sorry.

You are. OP = original poster. You started the thread.

---

