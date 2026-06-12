---
title: "help  problem install java"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by hgltqgs on 2008-04-04
hi all


i am write the code 
[PHP]
import javax.swing.JOptionPane;



public class Average1 {

   public static void main( String args[] )

   {

      int totle,gc,gv,av;

      String grade;

      totle = 0;

      gc = 1;

      while (gc <= 10 )

      {

         grade =JOptionPane.showInputDialog("enter intger grade: " );

        gv =Integer.parseInt(grade);

        totle = totle + gv;

        gc = gc + 1;

    }

        av= totle /10 ;

        JOptionPane.showMessageDialog(null, "Class avarge is " + av, "Class Avarage",JOptionPane.INFORMATION_MESSAGE );



        System.exit( 0 );

    }

}  [/PHP]


[PHP]
root@~# javac Average1.java
[/PHP]

[PHP]
root@~# java Average1
Exception in thread "main" java.lang.ClassFormatError: Average1 (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(natVMClassLoader.cc:78)
   at java.lang.ClassLoader.defineClass(ClassLoader.java:483)
   at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:108)
   at java.net.URLClassLoader.findClass(URLClassLoader.java:1171)
   at gnu.gcj.runtime.SystemClassLoader.findClass(natSystemClassLoader.cc:27)
   at java.lang.ClassLoader.loadClass(ClassLoader.java:351)
   at java.lang.ClassLoader.loadClass(ClassLoader.java:294)
   at gnu.java.lang.MainThread.run(MainThread.java:98)  [/PHP]

Erorr :confused:

---

### Post by hgltqgs on 2008-04-04
up :)

---

### Post by hgltqgs on 2008-04-05
up

---

### Post by hgltqgs on 2008-04-05
up End

---

