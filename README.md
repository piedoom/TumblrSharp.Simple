# TumblrSharp.Simple
A C# kit for accessing Tumblr's unauthenticated V1 API

# What is this?

Tumblr provides a few ways of accessing content.  Their new [V2 API](https://github.com/piedoom/TumblrSharp) is great for a rich user app, but it requires authentication and may not be the best solution for simple projects.

TumblrSharp.Simple is a PCL that allows for browsing Tumblr *without* authenticating.

# Installing

Search for `TumblrSharp.Simple` in [NuGet](https://www.nuget.org/packages/TumblrSharp.Simple/), or use your Package Manager Console.

```
PM> Install-Package TumblrSharp.Simple
```

# Examples

TumblrSharp.Simple provides a stateless static class, `TumblrClient`.

### Get the entirety of a page

```cs
var result = await TumblrClient.GetAllAsync("myblog");
```

### Get all of a specific post type

```cs
var result = await TumblrClient.GetPostsAsync<AudioPost>("myblog");
Console.WriteLine(result.Album);
```

### Get all posts

```cs
var result = await TumblrClient.GetPostsAsync("myblog");
```

### Get a specific post by ID

```cs
var result = await TumblrClient.GetPostAsync("myblog", 1237923847234);
```

# Caveats 

Tumblr's V1 API provides only one endpoint with all information.  Everything but the `GetAllAsync` method is just a helper method extracting requested data from `GetAllAsync`.
This means that `GetPostsAsync` will be as fast (or as slow) as `GetAllAsync`.
