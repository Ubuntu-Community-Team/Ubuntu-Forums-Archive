---
title: "sense simulator!"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by fellya on 2008-04-22
hello everyone!
I have got a problem in trying to compile c++ source codes by using gcc compiler but this using sense simulator.
I'm trying to use the tutorial found at [http://www.ita.cs.rpi.edu/sense/index.html](http://www.ita.cs.rpi.edu/sense/index.html) about how to compile.
I've installed both sense simulator and gcc compiler. when I put this command "cxx sim_routing.cc" i'm getting this kind of error: bash: cxx: command not found.
I need someone to help me to fix the problem.
thanks

---

### Post by fofo_star on 2009-02-04
hello every one i am also use sense simulator

the solution for cxx command not found as follow

suppose that sense simulator on drive c:/ and i am using cygwin environment then after building of the simulator 
you will find cxx.exe under
c:/sense-3.0.3/code/bin

to compile sim_routing.cc
go as follow
# cd c:/sense-3.0.3/code/examples/sense
# ../../bin/cxx sim_routing
you will get sim_routing.cxx in the same directory

then 
g++ -wall -o sim_routing sim_routing.cxx
but here sim_routing.exe does not found there are aproblem i need a solution for it please

---

### Post by ksudan on 2009-06-02
Use the following command in which the visualizer.a library needs to be linked.

g++ -Wall -o sim_routing sim_routing.cxx ../../libraries/visualizer/lib/libvisualizer.a

This library can be found under sense-3.0.3/code/libraries/visualizer/lib
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7390891")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7390891")

---

### Post by deswal on 2011-03-04
> **ksudan said:**
> Use the following command in which the visualizer.a library needs to be linked.

g++ -Wall -o sim_routing sim_routing.cxx ../../libraries/visualizer/lib/libvisualizer.a

This library can be found under sense-3.0.3/code/libraries/visualizer/lib
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7390891")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7390891")


Hello,
I compiled sim_routing.cc with command g++ sim_routing.cc -o sim_routing
Then i got errors such as mac/mac_80211.h , phy/transreciever.h etc. How these errors can be removed.

---

### Post by meenakshi525 on 2013-01-15
hello everyone!
i was running g-sense network simulator in windows 7 32-bit using cygwin. I was getting following error message while clicking run button in g-sense. Please anyone give a solution for this error.

Can we run g-sense in ubuntu. If we can, how to run?


See the end of this message for details on invoking 
just-in-time (JIT) debugging instead of this dialog box.

************** Exception Text **************
System.ComponentModel.Win32Exception: The system cannot find the file specified
   at System.Diagnostics.Process.StartWithCreateProcess(ProcessStartInfo startInfo)
   at System.Diagnostics.Process.Start()
   at System.Diagnostics.Process.Start(ProcessStartInfo startInfo)
   at G_Sense.FormAODV.buttonRunTest_Click(Object sender, EventArgs e) in D:\Pedro\Trabalhos_Ubi\NetGna\G-Sense\G-Sense\FormAODV.cs:line 241
   at System.Windows.Forms.Control.OnClick(EventArgs e)
   at System.Windows.Forms.Button.OnClick(EventArgs e)
   at System.Windows.Forms.Button.OnMouseUp(MouseEventArgs mevent)
   at System.Windows.Forms.Control.WmMouseUp(Message& m, MouseButtons button, Int32 clicks)
   at System.Windows.Forms.Control.WndProc(Message& m)
   at System.Windows.Forms.ButtonBase.WndProc(Message& m)
   at System.Windows.Forms.Button.WndProc(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.OnMessage(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.WndProc(Message& m)
   at System.Windows.Forms.NativeWindow.Callback(IntPtr hWnd, Int32 msg, IntPtr wparam, IntPtr lparam)


************** Loaded Assemblies **************
mscorlib
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.4952 (win7RTMGDR.050727-4900)
    CodeBase: file:///C:/Windows/Microsoft.NET/Framework/v2.0.50727/mscorlib.dll
----------------------------------------
G-Sense
    Assembly Version: 1.0.0.0
    Win32 Version: 1.0.0.0
    CodeBase: file:///D:/Softwares/Softwares/G-Sense/G-Sense.exe
----------------------------------------
System.Windows.Forms
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.4927 (NetFXspW7.050727-4900)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll
----------------------------------------
System
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.4927 (NetFXspW7.050727-4900)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System/2.0.0.0__b77a5c561934e089/System.dll
----------------------------------------
System.Drawing
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.4927 (NetFXspW7.050727-4900)
    CodeBase: file:///C:/Windows/assembly/GAC_MSIL/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
----------------------------------------

************** JIT Debugging **************
To enable just-in-time (JIT) debugging, the .config file for this
application or computer (machine.config) must have the
jitDebugging value set in the system.windows.forms section.
The application must also be compiled with debugging
enabled.

For example:

<configuration>
    <system.windows.forms jitDebugging="true" />
</configuration>

When JIT debugging is enabled, any unhandled exception
will be sent to the JIT debugger registered on the computer
rather than be handled by this dialog box.

---

