---
title: "Synaptic Package Manager no longer working"
date: 2024-01-27
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2024-01-27
Running Ubuntu 20.04 LTS and can't use Synaptic anymore. Always used Synaptic in the past with no problems.
Get this errror now with Synaptic being totally unresponsive: 
[IMG]https://i.postimg.cc/rmtvt6M3/Screenshot-from-2024-01-27-11-05-06.png[/IMG]

Tried to remove and re-install Synaptic with Ubuntu Software but it won't let me and gives me this message:
[IMG]https://i.postimg.cc/sXvZYcNt/Screenshot-from-2024-01-27-11-13-32.png[/IMG]

Can anyone help here?

---

### Post by Dennis N on 2024-01-27
I see it reporting an error in line 1 of /etc/apt/sources.list. The start of each line in there should be **deb** or  a #; **echo** is not recognized so it aborts.

---

### Post by MAFoElffen on 2024-01-27
I would first do
```

sudo apt install --reinstall synaptic

```
That would be assuming that your sources.list is pointing to the old-releases archive Repo's right?

Then I would backup what you have and upgrade the release from 16.04, to a recently supported version (Noticed the reference in the error to Xenial 16.04... That is way out of the official support range.

---

### Post by cybrsaylr on 2024-01-27
MAFoElffen, tried doing that. 

Put: sudo apt install --reinstall synaptic in terminal and got this below:

> Studio-XPS-8000:~$ sudo apt install --reinstall synaptic
[sudo] password for t: 
E: Type 'echo' is not known on line 1 in source list /etc/apt/sources.list.d/signal-xenial.list
E: The list of sources could not be read.
E: Type 'echo' is not known on line 1 in source list /etc/apt/sources.list.d/signal-xenial.list
E: The list of sources could not be read.
t@t-Studio-XPS-8000:~$ 


Don't have a clue what it means.

---

### Post by MAFoElffen on 2024-01-28
???

What is the output of this?
```

grep . /etc/apt/sources.list.d/signal-xenial.list

```

---

### Post by ajgreeny on 2024-01-28
Also let's see the output of```
cat /etc/apt/sources.list* | grep echo
``` which will show us the errant line in that file so we know if you need to delete the whole line or just the word **echo**

---

### Post by cybrsaylr on 2024-01-28
> **MAFoElffen said:**
> ???

What is the output of this?
```

grep . /etc/apt/sources.list.d/signal-xenial.list

```

Here it is:

> Studio-XPS-8000:~$ grep . /etc/apt/sources.list.d/signal-xenial.list
echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main' |\
  sudo tee /etc/apt/sources.list.d/signal-xenial.list
sudo apt update && sudo apt install signal-desktop
t@t-Studio-XPS-8000:~$ 


---

### Post by cybrsaylr on 2024-01-28
> **ajgreeny said:**
> Also let's see the output of```
cat /etc/apt/sources.list* | grep echo
``` which will show us the errant line in that file so we know if you need to delete the whole line or just the word **echo**

Here it is:

> Studio-XPS-8000:~$ cat /etc/apt/sources.list* | grep echo
cat: /etc/apt/sources.list.d: Is a directory
t@t-Studio-XPS-8000:~$ 



---

### Post by deadflowr on 2024-01-28
That's awesome.
You pasted the command into the file whole.

To fix I'd remove the file and run the command from the terminal
```
sudo rm /etc/apt/sources.list.d/signal-xenial.list

echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] https://updates.signal.org/desktop/apt xenial main' | sudo tee /etc/apt/sources.list.d/signal-xenial.list

sudo apt update
```

To run: copy each line I posted one at a time and paste it into the terminal and press enter.
So you will copy 3 lines and press enter a total of 4 times.
The first time you press enter will be to enter your password for sudo. So that adds an extra pressing of the enter key.
You only need to enter your password once for sudo, unless you've changed the sudoers timeout setting, which I doubt you have.

---

### Post by MAFoElffen on 2024-01-28
Or (harder) edit that file and remove the word echo and the errant single quotation marks. That is where that error is coming from.

deadflowr's solution is easier if you follow his directions!

---

### Post by ajgreeny on 2024-01-28
I apologise but my suggested **grep** command in post #6 was incorrect, as I was not thinking quickly nor in enough detail about what you needed.
It should have been ```
grep echo /etc/apt/*/*
```
This would have checked for the word *echo* in all the files in /etc/apt and its subfolders.

All should be good now anyway if you have done what **deadflowr** suggested.

It would be interesting to know how that extra word appeared in the file

---

### Post by deadflowr on 2024-01-28
> **MAFoElffen said:**
> Or (harder) edit that file and remove the word echo and the errant single quotation marks. That is where that error is coming from.

deadflowr's solution is easier if you follow his directions!

echo is just the first error.
They would have the other errors for the next line sudo tee >>> and then the line after that sudo apt >>>.
It's all wrong.

---

### Post by MAFoElffen on 2024-01-28
> **deadflowr said:**
> echo is just the first error.
They would have the other errors for the next line sudo tee >>> and then the line after that sudo apt >>>.
It's all wrong.
LOL. Yup. (Whatever installed that went western.)

---

### Post by cybrsaylr on 2024-01-29
> **deadflowr said:**
> To run: copy each line I posted one at a time and paste it into the terminal and press enter.
So you will copy 3 lines and press enter a total of 4 times.
The first time you press enter will be to enter your password for sudo. So that adds an extra pressing of the enter key.
You only need to enter your password once for sudo, unless you've changed the sudoers timeout setting, which I doubt you have.

Success!

Followed your instructions and it looks like Synaptic is working again.

Thanks for your help guys.

---

