The Gtk# website can be found at: http://www.mono-project.com/GtkSharp

Gtk# is a .NET language binding for the GTK+ toolkit and assorted GNOME
libraries. Gtk# is free software, licensed under the GNU LGPL.

Building & Installing Gtk#:
---------------------------

[![Join the chat at https://gitter.im/GLibSharp/GtkSharp](https://badges.gitter.im/GLibSharp/GtkSharp.svg)](https://gitter.im/GLibSharp/GtkSharp?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

    Install the gtk-3 development headers first. On Debian, this can be done using:
    apt-get install libgtk-3-dev

    We are using [meson](http://mesonbuild.com/) as a build system, you can build with

        meson build/
        ninja -C build/


The gui-thread-check profiler module.
-------------------------------------

    Since version 3 of gtk# a profiler called "gui-thread-check" is included as
    part of the install for debugging purposes. (It's located in the subfolder
    gtk/gui-thread-check .)

    This profiler module can be used to check if a GTK# application is trying to
    invoke gtk or gdk methods from a thread which is not the main GUI thread.

    To use it, run your application with the command:

        mono --profile=gui-thread-check yourapp.exe

    If the profiler is properly installed, you'll see an output like this:

        *** Running with gui-thread-check ***
        *** GUI THREAD INITIALIZED: 2861676352

    While the application is running, if the profiler detects a non-gui thread
    invoking gtk methods, it will print a warning message together with a
    stack trace. For example:

        *** GTK CALL NOT IN GUI THREAD: Widget.gtk_widget_get_parent
           Widget.get_Parent
           SourceEditorWidget.SetLastActiveEditor
           SourceEditorWidget.get_TextEditor
           SourceEditorWidget.get_Document
           SourceEditorWidget.HandleParseInformationUpdaterWorkerThreadDoWork
           BackgroundWorker.OnDoWork
           BackgroundWorker.ProcessWorker


Discussion & Support:
---------------------

    A mailing list for Gtk# discussion is available.

    You can subscribe to the mailing list by visiting:

        http://lists.ximian.com/mailman/listinfo/gtk-sharp-list

    And following the instructions (on that page) to subscribe.
    Messages are posted on this mailing list by sending them to:

        gtk-sharp-list@ximian.com

    (The mailing list requires you to subscribe in order to post
    messages.)

    An archive of this mailing list can be found at:

        http://lists.ximian.com/archives/public/gtk-sharp-list/

    Also, people can get help with and discuss Gtk# on IRC via the
    #gtk# or #mono channels on the irc.gnome.org IRC server.

    People looking for general help with C# should visit the
    #c# channel on irc.freenode.net IRC server.


Developers:
-----------

    For developers wishing to "get started" with Gtk#, they are encouraged
    to read the Mono Hand Book:

        http://www.mono-project.com/docs/gui/gtksharp/


Hackers:
--------

    For those who wish to help with the development of Gtk#, they should
    read the file named: HACKING.

    Also, anyone wishing to hack Gtk# is encouraged to join the Gtk#
    mailing list. And to visit the #gtk# IRC channel (on irc.gnome.org).
