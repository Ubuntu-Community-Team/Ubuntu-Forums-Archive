---
title: "nid help..How can I update my compiler?"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by blackblood357 on 2010-03-11
Pls help me..this our class exercise #3

I'm making a program using java now..and my compiler i think is not updated..i think it does not contain a library for jframe..

The terminal displayed:


jcalbances@RKOXP:~/Desktop/B3$ javac Calculator.java 
Calculator.java:4: warning: The serializable class Calculator does not declare a static final serialVersionUID field of type long
    public class Calculator extends JFrame {
                 ^^^^^^^^^^
Calculator.java:56: warning: The static field SwingConstants.VERTICAL should be accessed directly
    JToolBar vertical = new JToolBar(JToolBar.VERTICAL);
                                              ^^^^^^^^
2 problems (2 warnings)

---

### Post by tom4everitt on 2010-03-11
It does not give you an error, only warnings, hence it should work anyway i think.

About the warnings: The first one is common, I always ignore it :)

The second one can be fixed by switching line 56 to:

JToolBar vertical = new JToolBar(SwingConstants.VERTICAL);

I think. At least thats what the warning tells you to do: access VERTICAL directly.


(So I don't think you need to update your compiler actually.)

---

### Post by blackblood357 on 2010-03-11
Tnx for that man!:)

At least now my new problem is..

that the programs works but not correctly..

I cannot click the buttons and and the textbox won't even allow me to write.

I need to finish and submit this on monday. :confused:

---

### Post by tom4everitt on 2010-03-12
When a button is pressed, an ActionEvent is generated that needs to be picked up by a ActionListener...

There's usually a boolean for textboxes deciding whether they're writable or not.

---

