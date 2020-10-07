# nuget-mac-config
Setting up a private nuget repository on mac in visual studio

Using a Private NuGet Feed with VS for Mac

Visual Studio for Mac is a decent Integrated Development Environment (IDE) for writing .NET on a Mac. One area in which it has trouble is authenticating against a private NuGet feed. (For example, your company might host some common internal libraries). Attempting to configure a private NuGet feed using the Visual Studio for Mac IDE results in an endless authorization failure loop. See:

    https://developercommunity.visualstudio.com/content/problem/270269/vs-for-mac-repeatedly-ask-for-credentials-when-upd.html
    https://developercommunity.visualstudio.com/content/problem/120242/nuget-will-not-work-with-private-repos-401-errors.html

The solution is hidden away in a Microsoft document. In short, you must use NuGet V2 Application Programming Interface (API) feeds and a personal access token when accessing private NuGet feeds on a Mac.

First, select security from your Visual Studio online portal.

Then, you want to create a new Personal Access Token (PAT) with read-only packaging scope.

With your PAT, open a terminal and run the following command:


$ nuget sources add -name {your feed name} -source {your feed URL} 
-username {anything} -password {your PAT}

to add to visual studio in the nuget settings just enter the token in the password field

References:https://careers.hcss.com/using-a-private-nuget-feed-with-vs-for-mac/
