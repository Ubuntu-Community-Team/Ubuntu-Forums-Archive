---
title: "Application Menu Editor"
date: 2006-04-29
forum: Installation &amp; Upgrades
---

### Post by David Ranieri on 2006-04-29
I can't seem to add aegis to the Applications-> Acessories list.
I added it through add applications program and it's check box is ticked but still does not show up on the accessories list.

Any help would be appreciated.

---

### Post by Irony on 2006-04-29
The way to add to the menus (with programs that don't do this automatically) is to first find the path.

Open a terminal and type;

[PHP]aegis[/PHP]

If that doesn't start the program then type;

[PHP]whereis aegis[/PHP]

Note the path to the executable, lets say its;

[PHP]/usr/share/aegis[/PHP]

Type that in terminal to see if the program starts.

Once you've found the path to start the program, go to

*System Tools > Application Menu Editor*

Click where you want to add it say;

*Programming*

Click;

*New Entry*

Give it a Name and in the Command section type the path say;

[PHP]aegis[/PHP]

or;

[PHP]/usr/share/aegis[/PHP]

or whatever the path is. Click OK. Close the Editor.

---

### Post by David Ranieri on 2006-05-02
> **Irony]The way to add to the menus (with programs that don't do this automatically) is to first find the path.

Open a terminal and type said:**
> aegis[/PHP]

If that doesn't start the program then type;

[PHP]whereis aegis[/PHP]

Note the path to the executable, lets say its;

[PHP]/usr/share/aegis[/PHP]

Type that in terminal to see if the program starts.

Once you've found the path to start the program, go to

*System Tools > Application Menu Editor*

Click where you want to add it say;

*Programming*

Click;

*New Entry*

Give it a Name and in the Command section type the path say;

[PHP]aegis[/PHP]

or;

[PHP]/usr/share/aegis[/PHP]

or whatever the path is. Click OK. Close the Editor.
Open terminal
typing in aegis replay is: bash: aegis: command not found
typing command whereis aegis aegis:

---

### Post by Irony on 2006-05-02
Go to;

*System > Admin > Synaptic*

Search for aegis. Right click on aegis (note it should be green if its installed - if not install it), click properties and look for the path.

---

