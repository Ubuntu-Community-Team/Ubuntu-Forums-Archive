---
title: "Java getSystemLookAndFeelClassName() throws exception??"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dvlchd3 on 2010-04-28
I have tried using both OpenJDK and Sun's JDK, however, it seems the UIManager.getSystemLookAndFeelClassName() method throws an exception during runtime in 10.04RC.

My Code:
```

try {
    // Set System L&F
    UIManager.setLookAndFeel(
        UIManager.getSystemLookAndFeelClassName());
} 
catch (UnsupportedLookAndFeelException e) {
    e.printStackTrace();
}
catch (ClassNotFoundException e) {
    e.printStackTrace();
}
catch (InstantiationException e) {
    e.printStackTrace();
}
catch (IllegalAccessException e) {
    e.printStackTrace();
}

```

Commenting these lines out causes the application to start with the default Java Look and Feel (although the JPanels seem to have different vertical heights, as opposed to uniform heights when I run the application in WinXP.)

The stack trace:
```

Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at my.company.resources.ProblemButton.getName(ProblemButton.java:62)
	at com.sun.java.swing.plaf.gtk.GTKStyle.getInsets(GTKStyle.java:315)
	at javax.swing.plaf.synth.SynthStyle.installDefaults(SynthStyle.java:914)
	at javax.swing.plaf.synth.SynthLookAndFeel.updateStyle(SynthLookAndFeel.java:292)
	at javax.swing.plaf.synth.SynthButtonUI.updateStyle(SynthButtonUI.java:70)
	at javax.swing.plaf.synth.SynthButtonUI.installDefaults(SynthButtonUI.java:57)
	at javax.swing.plaf.basic.BasicButtonUI.installUI(BasicButtonUI.java:88)
	at javax.swing.JComponent.setUI(JComponent.java:651)
	at javax.swing.AbstractButton.setUI(AbstractButton.java:1799)
	at javax.swing.JButton.updateUI(JButton.java:143)
	at javax.swing.AbstractButton.init(AbstractButton.java:2166)
	at javax.swing.JButton.<init>(JButton.java:133)
	at javax.swing.JButton.<init>(JButton.java:106)
	at my.company.resources.ProblemButton.<init>(ProblemButton.java:26)
	at my.company.gui.TestSchedule.generateLines(TestSchedule.java:21)
	at my.company.gui.TestSchedule.<init>(TestSchedule.java:14)
	at my.company.gui.TestFront.<init>(TestFront.java:30)
	at my.company.gui.TestFront$1.run(TestFront.java:120)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

``` (Sorry had to change the package names until my employer authorizes me to release the code publicly, and then the company name will be excluded anyway.  My employer is very odd when it comes to software development and adopting new technologies...)

Since this is an issue with both OpenJDK and Sun's JDK, I assume there must be some problem with Java trying to get the Look and Feel from Lucid.  Does anyone have any insight on this issue?

---

