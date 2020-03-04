# Sketch frontend coding test

## Glossary

To understand the test, first you need to know two concepts:

- Document: a Sketch file that contains a design. A document can have N artboards, among other things that are not relevant to this test.
- Artboard: a type of layer that is used to contain other layers and displays a fixed frame on the Canvas. Usually they have a preset size. For instance, an iPhone X artboard has the size of an iPhone screen so you can place layers that builds your design in the artboard as they were on an iPhone.

A document usually has several artboards, each per a relevant page design: home screen, sign in screen, sign up screen, settings screen...

## Description

We want you to develop a document viewer for Sketch documents in the cloud with the following requirements.

This viewer must have two screens:

- Document page: Here, the user sees all artboards in the document. You need to show the artboards as thumbnails.
- Artboard page: Here, the user sees a particular artboard in a bigger size than in the document view.

Interactions:

- When the user views the document page and clicks on an artboard's thumbnail, the artboard page is loaded. The app shows the artboard full size, as described before.
- The user can navigate through the different artboards using the navigation controls in the top bar.
- The user can return to the document view clicking on the Close button in the left side of the top bar.

Notes:

- If the artboard image is bigger than the space available, it must get shrunk to fit on the screen.
- If the artboard image fits in the available space, show it in its original size.

## Images

**Document view**
![document](https://user-images.githubusercontent.com/1078228/74834572-fa7deb00-531b-11ea-921d-ea305910c544.png)

**Artboard view**
![Artboard](https://user-images.githubusercontent.com/1078228/74834589-01a4f900-531c-11ea-8290-dd851300dd50.png)

## Sketch file

You can check the design at https://sketch.cloud/s/z3p4o (see `Document` and `Artboard` artboards.)

You can play the prototype to get a better idea of what to develop.

You can download it, but there's no need to open it in the Sketch app. Implement the design in your web app the best you can.

## Assets

Here you'll find the icon assets of the design.
[assets.zip](https://github.com/sketch-hq/frontend-code-test/files/4235948/assets.zip)

## Data

The document that you must show has the shortId `Y8wDM`

Our API is based on GraphQL. The endpoint of our GraphQL API is `https://graphql.sketch.cloud/api`

You don't have to study the schema. Use the following query to get all the data that you need to render the application.

```graphql
{
  share(shortId: "Y8wDM") {
    shortId
    version {
      document {
        name
        artboards {
          entries {
            name
            isArtboard
            files {
              url
              height
              width
              scale
              thumbnails {
                url
                height
                width
              }
            }
          }
        }
      }
    }
  }
}
```

The requested document is a historical collection of different screens. An iPhone 3 home screen, a Xerox Alto screen, a Window vista screen... Each of those screens are on its own artboard, each one with its original size.

## Rules

- The application has to be developed using React.
- For styling, you can use whatever you want. We use styled components at Sketch, but feel free to use what you're more comfortable with.
- You can upload your solution to GitHub, GitLab, or the service of your preference. If, for privacy reasons, you don't want to publish anything, send us the repo in a ZIP file. Even if you send the code within a ZIP file, make sure it's a GIT repository, and we can see your gradual commits.
- We won't accept Pull Requests in this repo. Send us the link to your own repo or ZIP file as mentioned above to the mail address at the bottom of this file.
- Add a README.md file with the decisions you took, any information you want to share with us (possible improvements, for example), and the installation instructions. The app must work as expected following your instructions.
- We value our team life-work balance. Take the time you need to feel comfortable with your solution and do it at your own pace. If you feel that it's taking too much, stick to a basic implementation and tell us in the README.md how would you improve the code.

## What we will be looking for

- A nice architecture. Code is read more than it is written, so the easier it gets to follow your code, folder structure, etc... the better.
- Your UI composition. We'll check how you connect the different components of the application between them and how the data/state flows. Again, the easier for us to read it, the better.

## Bonus points

If you've finished the application as it's stated above, send us the code with no problems. But in case you want more challenges, you can add a couple of features (working on the bonus points won't necessarily make us value better your solution):

- Tests.
- Load different documents depending on the URL. In addition to the default document above, you can query for the one with the shortID `4W43q`

---

If you have any doubt, don't hesitate and send us an email (ivan@sketch.com or joanna@sketch.com)

We can't wait to see what you come up with! Thanks for your time!
